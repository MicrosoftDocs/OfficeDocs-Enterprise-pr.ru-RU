---
title: Минификация и объединение в SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: В этой статье описывается, как использовать иными и объединения методики с помощью Web Essentials сократить число HTTP-запросов и сократить время, необходимое для загрузки страниц в SharePoint Online.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542291"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Минификация и объединение в SharePoint Online

В этой статье описывается, как использовать иными и объединения методики с помощью Web Essentials сократить число HTTP-запросов и сократить время, необходимое для загрузки страниц в SharePoint Online.
  
Когда вы настраиваете свой веб-сайт, вы можете прийти к добавлению большого количества дополнительных файлов на сервер для поддержки этой настройки. Добавление дополнительных CSS- и JavaScript-файлов, изображений увеличивает количество HTTP-запросов на сервер, что в свою очередь увеличивает время, необходимое для отображения веб-страницы. Чтобы несколько файлов одного типа скачивались быстрее, их можно объединить.
  
Для JavaScript и CSS-файлов можно также использовать подход, называется иными, где уменьшить размер файлов путем удаления пробелов и других знаков, которых нет необходимости.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Минификация и объединение CSS- и JavaScript-файлов с помощью Web Essentials

Для объединения CSS- и JavaScript-файлов можно использовать программное обеспечение сторонних производителей, например Web Essentials.
  
> [!IMPORTANT]
> Основы Web является сторонних производителей, открытая, на основе сообщества project. Программное обеспечение — это расширение для Visual Studio 2012 и Visual Studio 2013 и не поддерживается корпорацией Майкрософт. Чтобы загрузить Web Essentials, посетите веб-сайте по [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
В Web Essentials доступны два формата для объединения:
  
- BUNDLE — для файлов CSS и JavaScript;
    
- SPRITE — для изображений (доступно только в Visual Studio 2013).
    
Вы можете использовать Web Essentials, если у вас есть функция с несколькими фирменными элементами, на которые ссылается пользовательская эталонная страница, например:
  
![Снимок экрана: элемент фирменной символики на настраиваемой эталонной странице](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Для создания пакета TE000127218 и CSS в Web Essentials**
  
1. В обозревателе решений в Visual Studio выберите файлы, которые нужно объединить.
    
2. Щелкните правой кнопкой мыши выбранных файлов, а затем выберите **Web Essentials** \> **файл пакета создания JavaScript** в контекстном меню. Например: 
    
    ![Снимок экрана: параметры меню Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Просмотр результатов объединения CSS- и JavaScript-файлов

Когда вы объединяете CSS- и JavaScript-файлы, Web Essentials создает XML-файл, называемый файлом инструкций. Он идентифицирует CSS- и JavaScript-файлы, а также некоторую другую информацию: 
  
![Снимок экрана: файл инструкций JavaScript и CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Кроме того, если в инструкции объединения значение флага минификации установлено как "true", то эти файлы будут уменьшены в размере и объединены. Это значит, что будут созданы новые, минифицированные версии JavaScript-файлов, на которые может ссылаться эталонная страница.
  
![Снимок экрана: флаг минификации со значением true](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Когда вы загружаете страницу со своего веб-сайта, вы можете использовать средства разработчика в своем веб-браузере, например Internet Explorer 11, чтобы увидеть количество запросов, отправленных на сервер, и время загрузки каждого файла.
  
На рисунке ниже представлен результат загрузки CSS- и JavaScript-файлов до минификации.
  
![Снимок экрана: скачивание 80 элементов](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
После объединения CSS- и JavaScript-файлов количество запросов сократилось до 74, а время загрузки файла только немного увеличилось по сравнению с загрузкой исходных файлов по отдельности:
  
![Снимок экрана: скачивание 74 элементов](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
После объединения JavaScript-файлы значительно уменьшились в размере (с 815 КБ до 365 КБ):
  
![Снимок экрана: сокращение размера скачиваемых элементов](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Объединение изображений путем создания спрайта изображений

Как и как объединяют файлы JavaScript и CSS, можно объединить множество небольших значки и другие общие изображения в увеличенного sprite и затем Показать отдельных изображений с помощью CSS. Вместо загрузки каждого отдельного изображения, веб-браузер пользователя загружает таблицы sprite один раз и кэширует его на локальном компьютере. Это повышает производительность загрузки страницы, снижают вниз на количество обращений к веб-сервера и файлы для загрузки.
  
 **Создание спрайта изображений в Web Essentials**
  
1. В обозревателе решений в Visual Studio выберите файлы, которые нужно объединить.
    
2. Щелкните правой кнопкой мыши выбранных файлов, а затем выберите **Web Essentials** \> **Создать изображение sprite** в контекстном меню. Например: 
    
    ![Снимок экрана: как создать спрайт изображения](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Выберите расположение для сохранения файла спрайта. SPRITE-файл — это XML-файл, описывающий настройки и файлы в спрайте. На следующих рисунках в качестве примера показаны файл спрайта в формате PNG и соответствующий ему XML-файл с расширением SPRITE.
    
    ![Снимок экрана: файл спрайта](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Снимок экрана: XML-файл спрайта](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  
