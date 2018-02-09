---
title: "DirSync для среды разработки и тестирования Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Сводка: Настройка синхронизации службы каталогов для Office 365 dev/тестовой среды."
ms.openlocfilehash: 32b9be8bb82d0efec2549dcacb5706c5e3dbc6f3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a>DirSync для среды разработки и тестирования Office 365

 **Сводка:** Настройка синхронизации каталогов для Office 365 dev/тестовой среды.
  
Во многих организациях используют Azure AD Connect и средство синхронизации службы каталогов (DirSync), чтобы синхронизировать набор учетных записей в локальном лесу Windows Server Active Directory (AD) с учетными записями в Office 365. В этой статье описывается добавление DirSync с синхронизацией паролей в среду тестирования и разработки Office 365, в результате чего получается следующая конфигурация:
  
![Среда разработки и тестирования Office 365 с DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Конфигурация состоит из следующих компонентов:  
  
- Пробная подписка Office 365 E5, которая действительна в течение 30 дней с момента создания.
    
- Упрощенная интрасеть организации, подключенная к Интернету и состоящая из трех виртуальных машин в подсети виртуальной сети Azure (DC1, APP1 и CLIENT1). Azure AD Connect работает на компьютере APP1 для синхронизации домена Windows Server AD с Office 365.
    
Процесс настройки этой среды разработки и тестирования состоит из двух указанных ниже основных этапов.
  
1. Создание среды разработки и тестирования Office 365 (виртуальных машин DC1, APP1 и CLIENT1 в виртуальной сети Azure с пробной подпиской Office 365 E5).
    
2. Установка и настройка Azure AD Connect на компьютере APP1.
    
> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Этап 1. Создание среды разработки и тестирования Office 365

Следуйте инструкциям в этапа 1, 2 и 3 в статье [Office 365 dev/тестовой среды](office-365-dev-test-environment.md) . Вот Результирующая конфигурация.
  
![Среда разработки и тестирования Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Конфигурация состоит из следующих компонентов:  
  
- Пробная подписка на Office 365 E5.
    
- Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Этап 2. Установка Azure AD Connect на компьютере APP1

После установки и настройки Azure AD Connect синхронизирует набор учетных записей на домене Windows Server AD CORP с учетными записями в пробной подписке Office 365. Описанная ниже процедура поможет вам установить средство Azure AD Connect на компьютере APP1 и убедиться, что оно работает.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Установка и настройка Azure AD подключение на APP1

1. С [Azure портала](https://portal.azure.com), подключиться к APP1 с CORP\\учетной записи User1.
    
2. В виртуальной машине APP1 откройте командную строку Windows PowerShell с правами администратора и выполните следующие команды:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. На панели задач нажмите кнопку **Internet Explorer** и перейдите к [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. На странице Microsoft Azure Active Directory подключения нажмите кнопку **загрузить**и нажмите кнопку **Запуск**.
    
5. На странице " **Добро пожаловать в Azure AD подключение** " нажмите кнопку **принимаю**и нажмите кнопку **Продолжить**.
    
6. На странице " **Быстрая** " щелкните **использовать параметры express**.
    
7. На странице " **подключение к Azure AD** " введите имя своей учетной записи глобального администратора в введите **имя пользователя,** пароль в поле **пароль**и нажмите кнопку **Далее**.
    
8. На странице **подключение к Доменные службы Active Directory** введите **CORP\\User1** в поле **имя пользователя** введите свой пароль в поле **пароль**и нажмите кнопку **Далее**.
    
9. На странице " **Конфигурация входа в Azure AD** " нажмите кнопку **Продолжить без подтвержденным домены**и нажмите кнопку **Далее**.
    
10. На странице **Готово к настройке** нажмите кнопку **Установить**.
    
11. На странице " **Настройка завершена** " нажмите кнопку **Выход**.
    
12. В Internet Explorer перейдите к порталу Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите пробной подписки Office 365 с учетной записью глобального администратора.
    
13. На главной странице портала щелкните **Администратор**.
    
14. На панели навигации слева выберите элементы **Пользователи > Активные пользователи**.
    
    Запомните учетную запись с именем **User1**. Эта учетная запись является из домена CORP Windows Server AD и обоснования работавших DirSync.
    
15. Нажмите кнопку учетной записи **User1** . Для лицензий на продукт нажмите кнопку **Изменить**.
    
16. В **лицензий на продукт**выберите страну и нажмите кнопку управления **Off** для **Office 365 корпоративный E5** (переключение к **на**). Нажмите кнопку **Сохранить** в нижней части страницы и нажмите кнопку **Закрыть**.
    
Ниже показана итоговая конфигурация.
  
![Среда разработки и тестирования Office 365 с DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Конфигурация состоит из следующих компонентов:  
  
- Пробная подписка на Office 365 E5.
    
- Упрощенная интрасеть организации, подключенная к Интернету и состоящая из виртуальных машин DC1, APP1 и CLIENT1 в подсети, входящей в виртуальную сеть Azure. Azure AD Connect работает на компьютере APP1 для синхронизации домена Windows Server AD CORP с Office 365 каждые 30 минут.
    
## <a name="next-step"></a>Следующий шаг

Если вы готовы к развертыванию DirSync для вашей организации, видеть [Развертывание Office 365 синхронизации каталогов (DirSync) в Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).

## <a name="see-also"></a>См. также

[Руководства по лаборатории тестирования для принятия облачных решений](cloud-adoption-test-lab-guides-tlgs.md)
  
[Базовая конфигурация среды разработки и тестирования](base-configuration-dev-test-environment.md)
  
[Среда разработки и тестирования Office 365](office-365-dev-test-environment.md)
  
[Облако безопасности приложения для Office 365 dev/тестовой среды](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Дополнительные защиту от угроз для вашей среды разработки или тестирования Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Освоение облака и гибридные решения](cloud-adoption-and-hybrid-solutions.md)




