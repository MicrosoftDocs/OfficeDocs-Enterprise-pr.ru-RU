---
title: Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Сводка: Используйте в этом документе Test Lab Guide Регистрация устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720415"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Регистрация устройств на базе ОС iOS и Android в среде разработки и тестирования Microsoft 365 корпоративный

 **Сводка:** В этом документе Test Lab Guide используйте для регистрации устройств в среде разработки и тестирования Microsoft 365 и удаленного управления.
  
Microsoft Enterprise мобильности Suite Командной помогает обеспечить вашим сотрудникам производительность пользователей с помощью своих избранные приложения и устройства защиты данных предприятия. Для получения дополнительных сведений см [мобильности Enterprise + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Если требуется применить защиту на уровне устройства, необходимо зарегистрировать устройств в Microsoft Intune. Регистрация устройств не только помогает управлять во владении организации устройств, но также личный (BYOD) и общих устройств, в зависимости от организации в юридических политик.
  
Выполнив инструкции, приведенные в этой статье, вы сможете регистрация и проверка возможности управления базовой мобильного устройства для iOS и Android в среде разработки и тестирования Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Этап 1: Создание Microsoft 365 dev/тестовой среды

Следуйте инструкциям в [Microsoft 365 Enterprise dev/тестовой среды](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Этап 2: Регистрация операций ввода-вывода и Android

Во-первых, используйте инструкции в [установки и войдите в приложение портала компании](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) для настройки приложения портала компании Майкрософт Intune для тестовой среды.

Затем используйте инструкции из статьи [Настройка доступа к ресурсам компании](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) для подачи заявок на устройстве операций ввода-вывода.

Затем используйте инструкции из статьи [Заявка Android устройство в Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) возможность зачисления Android устройства.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Этап 3: IOS и Android удаленного управления

Microsoft Intune предоставляет удаленного блокировки и код связи для сброса возможности. Если кто-то теряет свои устройства, можно заблокировать устройство удаленно. Если кто-то забудет их код связи, ее можно восстановить удаленно.
  
Чтобы заблокировать операций ввода-вывода или Android устройство удаленно:

1. Войдите в портал Azure в [https://portal.azure.com](https://portal.azure.com) с использованием учетных данных учетной записи глобального администратора.
2. Выберите **все службы**, введите **Intune**и нажмите кнопку **Intune**.
3. Нажмите кнопку **устройства > все устройства**.
4. В списке устройств нажмите кнопку операций ввода-вывода или Android устройства и нажмите кнопку действие **удаленного блокировки** .

    
Чтобы удаленно сбросить секретный код, сделайте следующее:

1. При необходимости, войдите в портал Azure в [https://portal.azure.com](https://portal.azure.com) с использованием учетных данных учетной записи глобального администратора.
2. Выберите **все службы**, введите **Intune**и нажмите кнопку **Intune**.
3. Нажмите кнопку **устройства > все устройства**.
4. В списке устройств, управление, щелкните операций ввода-вывода или Android устройство и выберите **... Дополнительные**. Выберите действие удаленных устройств **Удалить секретный код** .

Дополнительные экспериментов в разделе [действия из доступных устройств](https://docs.microsoft.com/intune/device-management#available-device-actions).

    

> [!TIP]
> Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.
  
## <a name="see-also"></a>См. также

[Среда разработки и тестирования Microsoft 365 корпоративный](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Политики MAM для вашей среды разработки и тестирования Microsoft 365 корпоративный](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Руководства по лаборатории тестирования для принятия облачных решений](cloud-adoption-test-lab-guides-tlgs.md)

[Мобильные решения на предприятиях + безопасности (Командной)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


