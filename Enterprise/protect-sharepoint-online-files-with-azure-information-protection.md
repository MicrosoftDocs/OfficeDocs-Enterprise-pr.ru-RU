---
title: "Защита файлов SharePoint Online с помощью Azure Information Protection"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Сводка. Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection."
ms.openlocfilehash: bc2c7dbbcc254270cf2c7db3d3eed98b3f7872f6
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Защита файлов SharePoint Online с помощью Azure Information Protection

 **Сводка.** Защита файлов на строго конфиденциальном сайте группы SharePoint Online с помощью службы Azure Information Protection.
  
В этой статье показано, как настроить Azure Information Protection, чтобы обеспечить шифрование и применение разрешений для файлов на строго конфиденциальном сайте группы SharePoint Online. Даже когда файл скачан с сайта, он остается защищен благодаря шифрованию и указанным разрешениям. Дополнительные сведения о строго конфиденциальных сайтах группы SharePoint Online см. в статье [Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Когда шифрование Azure Information Protection применяется к файлам в Office 365, служба не может обрабатывать содержимое этих файлов. Совместное редактирование, обнаружение электронных данных, поиск, Delve и другие функции совместной работы неактивны. Политики защиты от потери данных могут работать только с метаданными (включая метки Office 365), но не с содержимым этих файлов (например, номерами кредитных карт в файлах). 
  
Сперва выполните для настройки подписки на Office 365 действия, описанные в статье [Как активировать Azure RMS в Центре администрирования Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Теперь настройте Azure Information Protection, добавив новую политику области и подчиненную метку для разрешений на доступ к строго конфиденциальному сайту группы SharePoint Online и его защиты.
  
1. Войдите на портал Office 365, используя учетную запись с ролью администратора компании или администратора безопасности. Справочные сведения см. в статье [Вход в Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Перейдите на портал Azure ([https://portal.azure.com](https://portal.azure.com)), открыв отдельную вкладку браузера.
    
3. Если вы настраиваете Azure Information Protection впервые, ознакомьтесь с этими [инструкциями](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. На панели списка выберите **Дополнительные службы**, введите **Информация**, а затем выберите **Azure Information Protection**.
    
5. В колонке **Azure Information Protection**, щелкните последовательно элементы **Политики в области > + Добавить политику**.
    
6. Введите имя новой политики в поле **Имя политики** и описание в поле **Описание**.
    
7. Щелкните элементы **Выберите, к каким пользователям или группам будет применяться эта политика > Группы и пользователи**, а затем выберите группу доступа для участников строго конфиденциального сайта группы SharePoint Online. 
    
8. Щелкните элементы **Выбрать > ОК**.
    
9. Для метки **Строго конфиденциально** щелкните последовательно многоточие (…) и элемент **Добавить подчин. метку**.
    
10. Введите имя подчиненной метки в поле **Имя** и описание метки в поле **Описание**.
    
11. В разделе **Задайте разрешения для документов и электронных писем, имеющих эту метку** нажмите кнопку **Защитить**.
    
12. В разделе **Защита** выберите элемент **Azure (облачный ключ)**.
    
13. В колонке **Защита**, в разделе **Параметры защиты**, нажмите **+ Добавить разрешения**.
    
14. Перейдите к колонке **Добавление разрешений** и выберите **+ Обзор каталога** в разделе **Укажите пользователей и группы**.
    
15. В области **Пользователи и группы AAD** выберите группу доступа для членов строго конфиденциального сайта группы SharePoint Online, а затем нажмите **Выбрать**.
    
16. В разделе **Выбор разрешений из шаблона** снимите флажки **Печать**, **Копирование и извлечение контента** и **Переадресация**.
    
17. Дважды нажмите кнопку **ОК**.
    
18. В колонке **Подчиненная метка** нажмите кнопку **Сохранить**.
    
19. Закройте колонку новой политики области.
    
20. В колонке **Azure Information Protection  политики в области** нажмите кнопку **Опубликовать**.
    
Ниже показана полученная в результате конфигурация строго конфиденциального сайта группы SharePoint Online.
  
![Метка Azure Information Protection для изолированного сайта группы SharePoint Online.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Теперь вы можете создавать документы и защищать их с помощью службы Azure Information Protection и новой метки.
  
Необходимо [установить клиент Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) на мобильном устройстве или компьютере под управлением Windows. Вы можете воспользоваться скриптом и автоматизировать установку. Кроме того, пользователи могут установить клиент вручную. Просмотрите указанные ниже ресурсы.
  
- [Клиентская часть Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Руководство по клиенту Azure Information Protection для администратора](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Страница скачивания для установки вручную](https://www.microsoft.com/download/details.aspx?id=53018)
    
После установки пользователи выполняют запуск и вход из приложения Office (например, Microsoft Word) с указанием своей учетной записи Office 365. С помощью новой панели **Information Protection** пользователи могут выбрать новую метку. Убедитесь, что они знают, какую метку использовать для сайта группы SharePoint Online, чтобы защитить свои строго конфиденциальные файлы.
  
> [!NOTE]
> Если у вас несколько строго конфиденциальных сайтов группы SharePoint Online, необходимо создать несколько политик области Azure Information Protection с подчиненными метками, используя указанные выше параметры. При этом нужно настроить разрешения для каждой подчиненной метки, заданные группе доступа для участников определенного сайта группы SharePoint Online. 
  
## <a name="see-also"></a>См. также

[Безопасность сайтов и файлов SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Защита сайтов SharePoint Online в среде разработки и тестирования](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Руководство по безопасности (Майкрософт) для политических кампаний, некоммерческих и других динамических организаций](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)




