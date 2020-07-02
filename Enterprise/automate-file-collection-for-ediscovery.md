---
title: Автоматизация сбора файлов для обнаружения электронных данных
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: Сводка. Узнайте, как автоматизировать сбор файлов с компьютеров пользователей для обнаружения электронных данных.
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997980"
---
# <a name="automate-file-collection-for-ediscovery"></a>Автоматизация сбора файлов для обнаружения электронных данных

All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel. 
  
eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.
  
Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.
  
## <a name="what-this-solution-does"></a>Принцип работы решения

This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery. 
  
> [!IMPORTANT]
> This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file. 
  
На следующей схеме подробно рассмотрены все этапы и элементы решения.
  
![Обзор решения для автоматического сбора файлов](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****Условные обозначения****||
|:-----|:-----|
|![выноска пурпурного цвета 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Создайте объект групповой политики (GPO) и свяжите его со сценарием входа для сбора данных.  <br/> |
|![выноска пурпурного цвета 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Настройте фильтр безопасности GPO, чтобы применять объект групповой политики только к группе Custodians. <br/> |
|![выноска пурпурного цвета 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Хранитель входит в систему, после чего запускается GPO, вызывая сценарий входа для сбора данных.  <br/> |
|![выноска пурпурного цвета 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|Сценарий входа для сбора данных проводит инвентаризацию всех локально подключенных дисков на компьютере хранителя, ищет нужные файлы и записывает их расположение.  <br/> |
|![выноска пурпурного цвета 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|Сценарий входа для сбора данных копирует файлы, инвентаризация которых проведена, в скрытый файловый ресурс на промежуточном сервере.  <br/> |
|![выноска пурпурного цвета 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (Вариант А) Вручную запустите сценарий импорта PST-файлов, чтобы импортировать собранные PST-файлы в Exchange Server 2013. <br/> |
|![выноска пурпурного цвета 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Вариант б) С помощью средства и процесса импорта Microsoft 365 импортируйте собранные PST-файлы в Exchange Online.  <br/> |
|![выноска пурпурного цвета 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Переместите все собранные файлы в общую папку Azure для долгосрочного хранения с помощью модуля Runbook MoveToColdStorageSystem Center Orchestrator 2012 R2. <br/> |
|![выноска пурпурного цвета 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Индексируйте файлы в файловом ресурсе "холодного" хранилища с помощью SharePoint 2013.  <br/> |
|![выноска пурпурного цвета 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Выполните eDiscovery для контента в "холодном" хранилище и на локальном сервере Exchange Server 2013.  <br/> |
|![выноска пурпурного цвета 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Выполните обнаружение электронных данных для содержимого в Microsoft 365.  <br/> |
   
## <a name="prerequisites"></a>Предварительные условия

The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.
  
### <a name="base-configuration"></a>Базовая настройка

|**Элемент**|**Ссылка**|
|:-----|:-----|
|Домен Доменные службы Active Directory  <br/> ||
|Подключение к Интернету из локальной сети  <br/> ||
|SQL Server 2012 для поддержки SharePoint 2013 и System Center Orchestrator 2012 R2  <br/> |[Развертывание System Center Orchestrator 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| SharePoint 2013 в локальной среде или на основе Azure для eDiscovery (необходимо для варианта А) <br/> ||
|Локальный серверный файловый ресурс для промежуточного хранения  <br/> ||
|Локальный Exchange Server 2013 для импорта PST-файлов при использовании варианта А  <br/> |Накопительный пакет обновления 5 (15.913.22) доступен на [этой странице](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Развертывание System Center Orchestrator 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Microsoft 365 E3 с Exchange Online и SharePoint Online (необходимо для варианта б)  <br/> |Чтобы зарегистрировать подписку на Microsoft 365 E3, ознакомьтесь с [подпиской microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).  <br/> |
|Подписка на Azure с виртуальной машиной  <br/> |Сведения о подписке на Azure см. на странице [подписки на Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010). <br/> |
|VPN-подключение между локальной сетью и подпиской Azure  <br/> |Сведения о настройке туннеля VPN между службой Azure, предоставляемой по подписке, и локальной сетью см. в статье [Подключение локальной сети к виртуальной сети Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013eDiscovery, настроенное на поиск в SharePoint и Exchange Server 2013, а также (необязательно) Lync Server 2013  <br/> |Сведения о том, как настроить обнаружение электронных данных таким образом, см. в статье [Настройка обнаружения электронных данных в SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) и[руководстве по настройке обнаружения электронных данных для лаборатории тестирования общих папок Exchange, Lync, SharePoint и Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).    <br/> |
|Обнаружение электронных данных в Microsoft 365 для SharePoint Online и Exchange Online  <br/> |Чтобы настроить обнаружение электронных данных в Microsoft 365, ознакомьтесь со статьей [Настройка центра обнаружения электронных данных в SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Настройка среды

Теперь, когда базовая конфигурация готова, вы можете перейти к настройке самого решения. 
  
### <a name="staging-file-share"></a>Подготовка общей папки для промежуточного хранения

1. Создайте на локальном домене глобальную группу безопасности Custodians.
    
2. Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.
    
3. Задайте следующие разрешения для общей папки:
    
  - Хранители: "Изменение", "Чтение"
    
  - Администраторы: полный доступ
    
  - Доверенная подсистема Exchange: "Изменение", "Чтение"
    
4. Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:
    
  - **Тип: Deny**
    
  - **Применимо к: "Для этой папки, ее подпапок и файлов"**
    
5. Нажмите **Дополнительные разрешения** и выберите следующее:
    
  - **Чтение атрибутов**;
    
  - **Чтение дополнительных атрибутов**;
    
  - **Чтение разрешений**.
    
6. Проверьте доступ к общей папке Cases$. Для этого сделайте следующее:
    
1. Добавьте пользователя в группу Custodians.
    
2. Поместите файл в папку Cases$.
    
3. As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.
    
4. Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.
    
5. Try to open the file you previously placed in the share. This should fail.
    
### <a name="logon-script"></a>Сценарий входа

1. Скопируйте и вставьте этот сценарий Windows PowerShell в Блокнот:
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Сохраните приведенный выше сценарий как CollectionScript.ps1 в легкодоступном расположении, например C:\\AFCScripts.
    
3. Use the Go To feature in Notepad. Make the following changes, as needed:
    
|**Номер строки**|**Необходимые изменения**|**Обязательно?**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. <br/> |Необязательна  <br/> |
|76 и 77  <br/> |Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. <br/> |Необязательно  <br/> |
|80  <br/> |Переменную **$CaseRootLocation** необходимо настроить для общей папки коллекции промежуточных серверов, например **\\\\Staging\\Cases$**. <br/> |Обязательный  <br/> |
   
4. Поместите файл CollectionScript.ps1 в общую папку Netlogon на контроллере домена.  
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Настройте GPO для сценария входа и группы Custodians

1. Настройте сценарий входа для группы Custodians, следуя инструкциям из раздела "Как назначить сценарии входа пользователей" статьи [Использование сценариев запуска, завершения работы, входа и выхода в групповой политике](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Удалите пользователей, прошедших проверку подлинности, из раздела **Фильтры безопасности** и добавьте группу Custodians.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>Вариант А импорта PST-файлов, сценарий для Exchange Server 2013

1.  Скопируйте и вставьте следующий сценарий Windows PowerShell в Блокнот:
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.
    
3. Используя функцию Блокнота "Перейти", при необходимости внесите следующие изменения:
    
|**Номер строки**|**Необходимые изменения**|**Обязательно?**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. <br/> |Необязательный  <br/> |
|17   <br/> |**$ConnectionUri** необходимо настроить на отдельном сервере. <br/> > [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.          |Обязательно  <br/> |
   
4. Убедитесь, что у учетной записи "Доверенная подсистема Exchange" есть разрешения на чтение, запись и выполнение в общей папке \\\\Staging\\Cases$.
    
5. У сценария импорта PST-файлов есть два обязательных входных параметра:
    
  - **$SourcePath**  расположение импортируемых PST-файлов, например \\\\Staging\\Cases$.
    
  - **$MailboxAlias**  псевдоним целевого почтового ящика, в который будут импортированы элементы электронной почты.
    
6. Например, если вы хотите импортировать все PST-файлы из пути \\Staging\Cases$ в почтовый ящик с псевдонимом eDiscoveryMailbox, запустите следующий сценарий: `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Вариант Б импорта PST-файлов для Exchange Online

-  Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Автономное неструктурированное защищенное хранилище

1. Создайте общую папку в виртуальной машине Azure, в которую будут помещены все собранные файлы, например \\\\AZFile1\\ContentColdStorage.
    
2. Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Если планируется импортировать PST-файлы из общей папки \\\\AZFile1\\ContentColdStorage, предоставьте группе "Доверенная подсистема Exchange" разрешения на чтение, запись и выполнение в этой папке.
    
### <a name="orchestrator"></a>Orchestrator

1. Скачайте [MoveToColdStorage Runbook](https://go.microsoft.com/fwlink/?LinkId=616095) в Центре загрузки Майкрософт.
    
2. Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.
    
3. В поле **Расположение файла** введите путь и имя файла модуля Runbook, который вы хотите импортировать, или щелкните многоточие ( **...**), чтобы найти необходимый файл. 
    
4. Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.
    
5. Нажмите кнопку **Готово**.
    
6. Внесите в модуль Runbook **MoveFilesToColdStorage** следующие изменения.
    
1. **Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.
    
2. Действие **Удаление папки**: задайте в качестве значения параметра **Путь:** общую папку для сбора данных, например \\\\Staging\\cases$\\* и выберите пункт **Удалить все файлы и вложенные папки**. 
    
7. Разверните модуль Runbook **MoveToColdStorage**. Для этого выполните действия, перечисленные в статье[Развертывание модулей Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Локальный поиск защищенного хранилища в SharePoint

1. Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Использование решения

There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:
  
1. Управление членством в группе Custodians.
    
2. Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them
    
3. Управление процессом импорта PST-файлов.
    
4. Перемещение файлов коллекции в защищенное хранилище.
    
Все остальные действия не относятся к этому решению. Это стандартные административные задачи, выполняемые в SharePoint 2013, Microsoft 365 и Azure. В этом решении есть элементы, которые не предоставляют никаких рекомендаций, необходимых для работы, в зависимости от потребностей компании, например:
  
1. Отслеживание дел eDiscovery и связанных с ними хранителей.
    
2. Отслеживание связей наборов коллекций файлов и дел eDiscovery.
    
3. Согласование времени выполнения этапов импорта и перемещения в защищенное хранилище.
    
4. Управление размером файлов, используемых в службе Azure.
    
5. Управление почтовыми ящиками, в которые импортируются PST-файлы.
    
6. Резервное копирование и восстановление всех локальных данных.
    
### <a name="custodian-management"></a>Управление хранителями

- To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Отслеживание сбора файлов и просмотр файлов журнала

1. Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .
    
2. When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:
    
  - One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.
    
    > [!NOTE]
    > The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer. 
  
  - One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Вариант А импорта PST-файлов для Exchange Server 2013

1. Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.
    
3. Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Проверьте выходные данные на наличие ошибок.
    
5. Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Вариант Б импорта PST-файлов для Exchange Online

- Чтобы поместить собранные PST-файлы в Exchange Online, выполните процедуры, приведенные в файлах импорта, в Microsoft 365 с помощью [сетевой отправки](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).
    
### <a name="move-to-cold-storage"></a>Перемещение в защищенное хранилище

1. Запустите Runbook **MoveToColdStorage** , используя процедуры в [запущенных модулях Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.
    
### <a name="ediscovery"></a>Обнаружение электронных данных

1. Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Создайте обращение к функции "eDiscovery" в SharePoint 2013, если вы использовали вариант А для импорта PST-файлов, или обращение к функции "eDiscovery" в SharePoint Online, если использовался вариант Б.
    

