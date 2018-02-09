---
title: "Cloud App Security для среды разработки и тестирования Office 365"
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
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Сводка. Настройка и демонстрация работы Office 365 Cloud App Security в среде разработки и тестирования Office 365."
ms.openlocfilehash: b13931ca21b440188563feef9236cd70e6df084b
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="23814-103">Cloud App Security для среды разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="23814-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="23814-104">**Сводка.** Настройка и демонстрация работы Office 365 Cloud App Security в среде разработки и тестирования Office 365.</span><span class="sxs-lookup"><span data-stu-id="23814-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="23814-p101">Office 365 Cloud App Security (предыдущее название  расширенное управление безопасностью Office 365) позволяет создавать политики, которые отслеживают подозрительные действия в вашей подписке на Office 365 и сообщают вам о них, чтобы вы могли исследовать и исправить проблему. Дополнительные сведения см. в статье [Обзор Cloud App Security в Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="23814-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="23814-107">С помощью инструкций в этой статье вы можете включить и протестировать функции Cloud App Security в пробной подписке на Office 365.</span><span class="sxs-lookup"><span data-stu-id="23814-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="23814-108">Щелкните [здесь](http://aka.ms/catlgstack), чтобы просмотреть схему всех статей, относящихся к руководствам по лаборатории тестирования Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="23814-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="23814-109">Этап 1. Создание среды разработки и тестирования Office 365 — упрощенной или для имитированных предприятий</span><span class="sxs-lookup"><span data-stu-id="23814-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="23814-110">Если вам нужно лишь упрощенное (с минимальными требованиями) тестирование Cloud App Security, следуйте инструкциям в статье [Среда разработки и тестирования Office 365](office-365-dev-test-environment.md) (этапы 2 и 3).</span><span class="sxs-lookup"><span data-stu-id="23814-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="23814-111">Если вы хотите протестировать Cloud App Security на имитированном предприятии, выполните действия, описанные в статье [DirSync для среды разработки и тестирования Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="23814-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="23814-p102">Чтобы можно было протестировать Cloud App Security, не требуется среда разработки и тестирования для имитированного предприятия, предусматривающая подключение имитированной интрасети к Интернету и синхронизацию каталогов для леса Windows Server AD. Она указана здесь лишь для того, чтобы вы могли протестировать Cloud App Security и поэкспериментировать с этим компонентом в типичной для организаций среде.</span><span class="sxs-lookup"><span data-stu-id="23814-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="23814-114">Этап 2. Перед включением Cloud App Security и созданием политики</span><span class="sxs-lookup"><span data-stu-id="23814-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="23814-115">В этой процедуре показано, что, пока не включена служба Cloud App Security, глобальному администратору не приходят уведомления по электронной почте об изменениях в ролях пользователей.</span><span class="sxs-lookup"><span data-stu-id="23814-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="23814-116">Проверка режима работы уведомлений по умолчанию в Office 365</span><span class="sxs-lookup"><span data-stu-id="23814-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="23814-117">Перейдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите на странице пробной подписки на Office 365, используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="23814-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="23814-118">Если вы используете упрощенную среду разработки и тестирования Office 365, войдите с локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="23814-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="23814-119">Если вы используете среду разработки и тестирования Office 365 для имитированного предприятия, войдите на [портал Azure](https://portal.azure.com), чтобы подключиться к виртуальной машине CLIENT1, а затем выполните вход с этой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="23814-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="23814-120">На главной странице портала щелкните **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="23814-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="23814-121">На панели навигации слева выберите элементы **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="23814-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="23814-122">Выберите учетную запись **Пользователь 4**.</span><span class="sxs-lookup"><span data-stu-id="23814-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="23814-123">На странице **Пользователь 4** щелкните **Изменить** в строке **Роли**.</span><span class="sxs-lookup"><span data-stu-id="23814-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="23814-p103">На странице **Изменить роли пользователя** выберите пункт **Глобальный администратор**, введите **user4@contoso.com** в поле для **дополнительного электронного адреса** и нажмите кнопку **Сохранить**. Щелкните **Закрыть** дважды.</span><span class="sxs-lookup"><span data-stu-id="23814-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="23814-126">В левом верхнем углу нажмите значок запуска приложений и выберите элемент **Почта**.</span><span class="sxs-lookup"><span data-stu-id="23814-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="23814-p104">Подождите 30 минут. Обратите внимание, что вам как глобальному администратору не пришло уведомление по электронной почте об изменении в роли Пользователя 4.</span><span class="sxs-lookup"><span data-stu-id="23814-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="23814-129">Этап 3. Включение Cloud App Security и создание политики</span><span class="sxs-lookup"><span data-stu-id="23814-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="23814-p105">В этой процедуре показано, как включить Cloud App Security и создать новую политику для отправки глобальному администратору по электронной почте уведомлений об изменениях в ролях пользователей. Что для этого нужно:</span><span class="sxs-lookup"><span data-stu-id="23814-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="23814-132">Имя и пароль учетной записи глобального администратора пробной подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="23814-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="23814-133">Имя и пароль учетной записи Пользователя 5 пробной подписки на Office 365.</span><span class="sxs-lookup"><span data-stu-id="23814-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="23814-134">Включение и настройка Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="23814-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="23814-135">Перейдите на портал Office 365 ([https://portal.office.com](https://portal.office.com)) и войдите на странице пробной подписки на Office 365, используя учетную запись глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="23814-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="23814-136">Нажмите плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="23814-136">Click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="23814-137">В области навигации слева выберите **Оповещения > Управление расширенными оповещениями**.</span><span class="sxs-lookup"><span data-stu-id="23814-137">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="23814-138">На странице **Управление расширенными оповещениями** нажмите **Включить Office 365 Cloud App Security**, а затем выберите **Перейти к Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="23814-138">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="23814-139">На вкладке **Панель мониторинга** выберите **Элемент управления > Политики**.</span><span class="sxs-lookup"><span data-stu-id="23814-139">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="23814-140">На странице **Политики** нажмите **Создание политики** и выберите элемент **Политика действий**.</span><span class="sxs-lookup"><span data-stu-id="23814-140">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="23814-141">В поле **Имя политики** введите **Административное действие**.</span><span class="sxs-lookup"><span data-stu-id="23814-141">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="23814-142">В разделе **Серьезность политики** выберите **Высокая**.</span><span class="sxs-lookup"><span data-stu-id="23814-142">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="23814-143">В разделе **Категория** выберите элемент **Привилегированные учетные записи**.</span><span class="sxs-lookup"><span data-stu-id="23814-143">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="23814-144">В разделе **Создать фильтры для политики** для элемента **Действия, соответствующие всем следующим условиям** задайте значение **Административное действие**.</span><span class="sxs-lookup"><span data-stu-id="23814-144">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="23814-p106">В разделе **Оповещения** выберите **Отправлять оповещение по электронной почте**. В поле **Кому** введите адрес электронной почты учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="23814-p106">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="23814-147">В нижней части страницы нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="23814-147">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="23814-148">Этап 4. Демонстрация Cloud App Security в действии</span><span class="sxs-lookup"><span data-stu-id="23814-148">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="23814-149">В этой процедуре показано, как Cloud App Security создает оповещения и отправляет уведомления по электронной почте глобальному администратору, когда Пользователь 4 делает Пользователя 5 администратором по паролям и управлению пользователями.</span><span class="sxs-lookup"><span data-stu-id="23814-149">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="23814-150">Демонстрация уведомления по электронной почте об изменении в ролях учетных записей пользователей</span><span class="sxs-lookup"><span data-stu-id="23814-150">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="23814-151">Щелкните значок пользователя в верхней правой части страницы, а затем выберите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="23814-151">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="23814-152">Перейдите по такому адресу: [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="23814-152">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="23814-153">На странице входа в Office 365 выберите пункт **Используйте другую учетную запись**.</span><span class="sxs-lookup"><span data-stu-id="23814-153">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="23814-154">Введите имя и пароль учетной записи Пользователя 4 и нажмите кнопку **Войти**.</span><span class="sxs-lookup"><span data-stu-id="23814-154">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="23814-155">При необходимости измените пароль учетной записи Пользователя 4, а затем нажмите **Сменить пароль и войти в систему**.</span><span class="sxs-lookup"><span data-stu-id="23814-155">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="23814-156">На странице портала Office 365 выберите **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="23814-156">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="23814-157">Если нужно, нажмите **Отмена** при запросе на обновление контактных данных для администратора.</span><span class="sxs-lookup"><span data-stu-id="23814-157">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="23814-158">На главной странице портала щелкните **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="23814-158">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="23814-159">На панели навигации слева выберите элементы **Пользователи > Активные пользователи**.</span><span class="sxs-lookup"><span data-stu-id="23814-159">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="23814-160">Выберите учетную запись **Пользователь 5**.</span><span class="sxs-lookup"><span data-stu-id="23814-160">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="23814-161">На странице **Пользователь 5** щелкните **Изменить** в строке **Роли**.</span><span class="sxs-lookup"><span data-stu-id="23814-161">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="23814-p107">На странице **Изменить роли пользователя** выберите **Настраиваемый администратор**, затем **Администратор паролей** и **Администратор управления пользователями**, введите **user5@contoso.com** в поле **Дополнительный электронный адрес** и нажмите кнопку **Сохранить**. Щелкните **Закрыть** дважды.</span><span class="sxs-lookup"><span data-stu-id="23814-p107">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="23814-164">Щелкните значок пользователя в верхней правой части страницы, а затем выберите **Выйти**.</span><span class="sxs-lookup"><span data-stu-id="23814-164">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="23814-165">Перейдите по такому адресу: [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="23814-165">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="23814-166">На странице **входа в Office 365** выберите имя учетной записи глобального администратора.</span><span class="sxs-lookup"><span data-stu-id="23814-166">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="23814-167">Введите пароль и нажмите кнопку **Войти**.</span><span class="sxs-lookup"><span data-stu-id="23814-167">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="23814-168">На главной странице портала щелкните **Администратор**.</span><span class="sxs-lookup"><span data-stu-id="23814-168">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="23814-169">Нажмите плитку **Безопасность и соответствие требованиям**.</span><span class="sxs-lookup"><span data-stu-id="23814-169">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="23814-170">В области навигации слева выберите **Оповещения > Управление расширенными оповещениями**.</span><span class="sxs-lookup"><span data-stu-id="23814-170">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="23814-171">На странице **Управление расширенными оповещениями** выберите **Перейти к Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="23814-171">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="23814-172">На новой вкладке **Панель мониторинга** вы увидите два оповещения для элемента **Административное действие**.</span><span class="sxs-lookup"><span data-stu-id="23814-172">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="23814-p108">На главной вкладке **Microsoft Office** щелкните **Почта**. Возможно, придется подождать до 30 минут.</span><span class="sxs-lookup"><span data-stu-id="23814-p108">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="23814-p109">В папке "Входящие" вы увидите два новых электронных сообщения, в названии которых указано **Служба уведомлений Microsoft Azure AD**. В одном из сообщений говорится, что учетной записи Пользователя 5 присвоена роль **Администратор паролей**. В другом сообщении указано, что учетной записи Пользователя 5 присвоена роль **Администратор пользователей** (приравнивается к роли администратора управления пользователями в Центре администрирования Office 365).</span><span class="sxs-lookup"><span data-stu-id="23814-p109">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="23814-p110">Теперь с помощью этой среды можно создавать новые политики и продолжать экспериментировать с Office 365 Cloud App Security. Ссылки на дополнительные статьи, посвященные конфигурации, см. на странице [Начало работы с Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).</span><span class="sxs-lookup"><span data-stu-id="23814-p110">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23814-179">См. также</span><span class="sxs-lookup"><span data-stu-id="23814-179">See Also</span></span>

[<span data-ttu-id="23814-180">Руководства по лаборатории тестирования для принятия облачных решений</span><span class="sxs-lookup"><span data-stu-id="23814-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="23814-181">Среда разработки и тестирования Office 365</span><span class="sxs-lookup"><span data-stu-id="23814-181">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="23814-182">Освоение облака и гибридные решения</span><span class="sxs-lookup"><span data-stu-id="23814-182">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="23814-183">Обзор Cloud App Security в Office 365</span><span class="sxs-lookup"><span data-stu-id="23814-183">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


