---
title: Développement mobile multiplateforme dans Visual Studio | Microsoft Docs
description: Dans cet article, Découvrez comment vous pouvez créer des applications pour les appareils Android, iOS et Windows à l’aide de Visual Studio.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 2f3c611ae157be4f2ea89254856bdd3b6fba448d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687681"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Développement mobile multiplateforme dans Visual Studio

Vous pouvez créer des applications pour des appareils Android, iOS et Windows à l'aide de Visual Studio.  Lorsque vous concevez votre application, utilisez les outils de Visual Studio pour ajouter facilement des services connectés tels que Microsoft 365, Azure App Service et Application Insights.

Créez vos applications en utilisant C# et le .NET Framework, HTML et JavaScript, ou C++. Partagez du code, des chaînes, des images et même, dans certains cas, l’interface utilisateur.

Si vous souhaitez créer un jeu ou une application graphique immersive, installez les Visual Studio Tools pour Unity et profitez de toutes les puissantes fonctionnalités de productivité de Visual Studio avec Unity, un moteur de jeu/moteur graphique multiplateforme très répandu, qui est aussi un environnement de développement pour les applications qui s’exécutent sur iOS, Android, Windows et d’autres plateformes.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Générer une application pour Android, iOS et Windows (.NET Framework)

![Appareils](../cross-platform/media/homedevices.png "HomeDevices")

Avec Visual Studio Tools pour Xamarin, vous pouvez cibler Android, iOS et Windows dans la même solution, tout en partageant du code et même l’IU.

|**En savoir plus**|
|--------------------|
|[Installer Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[En savoir plus sur Xamarin dans Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Documentation sur le développement d’applications mobiles Xamarin](/xamarin/) |
|[DevOps avec les applications Xamarin](/xamarin/tools/ci/devops/) |
|[En savoir plus sur les applications Windows universelles dans Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[En savoir plus sur les similitudes entre Swift et C#](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Cibler Android, iOS et Windows à partir d’une seule base de code

 Vous pouvez créer des applications natives pour Android, iOS et Windows en C# ou F # (Visual Basic n’est pas pris en charge pour l’instant).  Pour commencer, installez Visual Studio, puis sélectionnez l’option **développement mobile avec .net** dans le programme d’installation.

 Si vous avez déjà installé Visual Studio, réexécutez le **Visual Studio installer** et sélectionnez la même option **mobile Development with .net** pour Xamarin (comme ci-dessus).

 Une fois que vous avez terminé, les modèles de projet s’affichent dans la boîte de dialogue **Nouveau projet**. La meilleure façon de trouver des modèles Xamarin consiste à effectuer simplement une recherche sur « Xamarin ».

 Xamarin expose les fonctionnalités natives d’Android, d’iOS et de Windows en tant que classes et méthodes .NET. Ainsi, vos applications ont un accès total aux API natives et aux contrôles natifs. Elles sont tout aussi réactives que les applications écrites dans les langages de plateforme natifs.

 Après avoir créé un projet, vous pourrez profiter de toutes les fonctionnalités de productivité de Visual Studio. Par exemple, vous allez utiliser un concepteur pour créer vos pages, et la fonctionnalité IntelliSense pour explorer les API natives des plateformes mobiles. Une fois que vous êtes prêt à exécuter votre application pour voir à quoi elle ressemble, vous pouvez utiliser l’émulateur du kit Android SDK et exécuter les applications Windows en mode natif. Vous pouvez également utiliser directement des appareils Android et Windows attachés. Pour les projets iOS, connectez-vous à un Mac en réseau et démarrez l’émulateur iOS à partir de Visual Studio, ou connectez-vous à un appareil attaché.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Concevoir un ensemble de pages qui s'affichent sur tous les appareils à l'aide de Xamarin.Forms

 Selon la complexité de la conception de vos applications, vous pouvez envisager de les créer en utilisant les modèles *Xamarin.Forms* du groupe de modèles de projet **Applications mobiles** . Xamarin.Forms est un kit de ressources d’IU qui vous permet de créer une interface utilisateur que vous pouvez partager sur Android et iOS, ainsi que sur Windows Phone.  Quand vous compilez une solution Xamarin.Forms, vous obtenez une application Android, une application iOS et une application Windows. Pour plus d’informations, consultez [En savoir plus sur le développement mobile avec Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) et la [documentation Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Partager du code entre des appareils Android, iOS et Windows

 Si vous n’utilisez pas Xamarin.Forms et que vous choisissez de concevoir pour chaque plateforme individuellement, vous pouvez partager la plus grande partie du code autre que celui de l’interface utilisateur entre les projets des différentes plateformes (iOS, Android et Windows). Cela inclut la logique métier, l'intégration du cloud, l'accès aux bases de données ou tout autre code qui cible le .NET Framework. Le seul code que vous ne pouvez pas partager est le code qui cible une plateforme spécifique.

 ![Partager du code entre des interfaces utilisateur Windows, iOS et Android](../cross-platform/media/sharecode.png "ShareCode")

 Vous pouvez partager votre code en utilisant un projet partagé, un projet de bibliothèque de classes portables ou les deux. Vous trouverez peut-être qu'une partie du code est mieux placé dans un projet partagé, et que d'autres parties ont davantage de sens placées dans un projet de bibliothèque de classes portables.

|**En savoir plus**|
|--------------------|
|[Sharing Code Options](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Options de partage du code avec .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Cibler des appareils Windows 10

 ![Appareils Windows](../cross-platform/media/windowsdevices.png "Périphériques Windows")

 Si vous voulez créer une application unique qui cible la totalité des appareils Windows 10, créez une application Windows universelle. Vous allez concevoir l’application à l’aide d’un seul projet, et vos pages s’afficheront correctement, quel que soit l’appareil utilisé pour les visualiser.

 Commencez avec un modèle de projet d’application UWP (plateforme Windows universelle). Concevez vos pages visuellement, puis ouvrez-les dans une fenêtre d'aperçu pour voir comment elles apparaissent sur les différents types d'appareils. Si vous n’aimez pas la façon dont une page apparaît sur un appareil, vous pouvez optimiser cette page pour qu’elle soit mieux adaptée à la taille d’écran, à la résolution ou aux différentes orientations, comme le mode paysage ou le mode portrait. Vous pouvez faire tout cela à l'aide des fenêtres d'un outil intuitif et des options de menu facilement accessibles dans Visual Studio. Quand vous êtes prêt à exécuter votre application et à avancer pas à pas dans votre code, vous avez à votre disposition tous les émulateurs et simulateurs pour différents types d’appareils dans une seule liste déroulante, qui se trouve sur la barre d’outils **Standard**.

|**En savoir plus**|
|--------------------|
|[Introduction à la plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide)|
|[Créer votre première application](/windows/uwp/get-started/your-first-app)|
|[Développer des applications pour la plateforme Windows universelle (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Créer une application pour Android, iOS et Windows (HTML/JavaScript)

 ![Appareils Windows, iOS et Android](../cross-platform/media/homedevices.png "Appareils Windows, iOS et Android")

 Si vous êtes un développeur web et que vous connaissez bien les langages HTML et JavaScript, vous pouvez cibler Windows, Android et iOS en utilisant Visual Studio Tools pour Apache Cordova. Ces applications peuvent cibler les trois plateformes et vous pouvez les créer en utilisant les compétences et les processus qui vous sont les plus familiers.

 Apache Cordova est un framework qui inclut un modèle de plug-in. Ce modèle de plug-in fournit une seule API JavaScript qui vous permet d’accéder aux fonctionnalités natives des appareils des trois plateformes (Android, iOS et Windows).

 Étant donné que ces API sont multiplateformes, vous pouvez partager la plus grande partie de ce que vous écrivez entre les trois plateformes. Ceci permet de réduire les coûts de développement et de maintenance. En outre, il est inutile de tout reprendre à zéro. Si vous avez créé d’autres types d’applications web, vous pouvez partager ces fichiers avec votre application Cordova sans avoir à les modifier ou à les reconcevoir d’une quelconque façon.

 ![Applications hybrides multi-appareils avec JavaScript](../cross-platform/media/multidevicehybridapps.png "Applications hybrides multi-appareils avec JavaScript")

 Pour commencer, installez Visual Studio, puis choisissez la fonctionnalité **Développement mobile en JavaScript** au cours de l’installation. Les Outils Cordova installent automatiquement l’ensemble des logiciels tiers nécessaires pour générer votre application multiplateforme.

 Une fois que vous avez installé l’extension, ouvrez Visual Studio et créez un projet **Application vide (Apache Cordova)** . Ensuite, vous pouvez développer votre application en utilisant JavaScript ou TypeScript. Vous pouvez aussi ajouter des plug-ins pour étendre les fonctionnalités de votre application. Les API des plug-ins s'affichent alors dans IntelliSense quand vous écrivez du code.

 Quand vous êtes prêt à exécuter votre application et votre code pas à pas, choisissez un émulateur, par exemple Apache Ripple ou l’Émulateur Android, un navigateur ou un appareil que vous avez connecté directement à votre ordinateur. Ensuite, démarrez votre application. Si vous développez votre application sur un ordinateur Windows, vous pouvez même l’exécuter sur cet ordinateur. Toutes ces options sont intégrées à Visual Studio via Visual Studio Tools pour Apache Cordova.

 Les modèles de projet pour la création d’applications UWP (plateforme Windows universelle) sont toujours disponibles dans Visual Studio. N’hésitez pas à les utiliser si vous prévoyez de cibler uniquement des appareils Windows. Si vous décidez plus tard de cibler Android et iOS, vous pouvez toujours porter votre code vers un projet Cordova.

|**En savoir plus**|
|--------------------|
|[Installer Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Bien démarrer avec Visual Studio Tools pour Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[En savoir plus sur l’émulateur Visual Studio pour Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Créer une application pour Android, iOS et Windows (C++)

![Utiliser C&#43;&#43; pour créer des appareils Android, iOS et Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Tout d’abord, installez Visual Studio et le **développement mobile avec** la charge de travail C++. Ensuite, vous pouvez créer une application d’activité native pour Android ou une application qui cible Windows ou iOS. Vous pouvez cibler Android, iOS et Windows dans la même solution si vous le souhaitez, puis partager du code entre eux à l’aide d’une bibliothèque partagée statique ou dynamique multiplateforme.

 Si vous devez générer une application pour Android qui nécessite toute sorte de manipulations graphiques avancées (par exemple un jeu), vous pouvez le faire en C++. Commencez par le projet d' **application d’activité native (Android)** . Ce projet offre une prise en charge complète de la chaîne d'outils Clang.

 ![Modèle de projet d'activité native](../cross-platform/media/cross-plat_cpp_native.png "Modèle de projet d'activité native")

 Une fois que vous êtes prêt à exécuter votre application pour voir à quoi elle ressemble, utilisez l’Émulateur Android. Il est rapide, fiable, et facile à utiliser et à configurer.

 Vous pouvez également créer une application qui cible l’intégralité des appareils Windows 10 en utilisant C++ et un modèle de projet d’application UWP (plateforme Windows universelle). Pour en savoir plus sur cette question, consultez la section [Cibler les appareils Windows 10](#WindowsHTML) plus haut dans cette rubrique.

 Vous pouvez partager du code C++ entre Android, iOS et Windows en créant une bibliothèque partagée statique ou dynamique.

 ![Bibliothèques partagées statiques et dynamiques](../cross-platform/media/cross_plat_cpp_libraries.png "Bibliothèques partagées statiques et dynamiques")

 Vous pouvez utiliser cette bibliothèque dans un projet Windows, iOS ou Android, comme ceux décrits plus haut dans cette section. Vous pouvez également l'utiliser dans une application que vous créez à l'aide de Xamarin, Java ou n'importe quel langage qui vous permet d'appeler des fonctions dans une DLL non managée.

 Lorsque vous écrivez le code dans ces bibliothèques, vous pouvez utiliser IntelliSense pour explorer les API natives des plateformes Android et Windows. Ces projets de bibliothèque sont entièrement intégrés au débogueur Visual Studio, de sorte que vous pouvez définir des points d'arrêt, parcourir le code, et rechercher et résoudre les problèmes à l'aide de toutes les fonctionnalités avancées du débogueur.

|**En savoir plus**|
|--------------------|
|[Télécharger Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Installer le développement mobile multiplateforme avec C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[En savoir plus sur l’utilisation de C++ pour cibler plusieurs plateformes](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Installer ce dont vous avez besoin, puis créer une application d’activité Native C++ pour Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[En savoir plus sur le partage de code C++ avec les applications Android et Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Exemples de développement mobile multiplateforme pour C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Générer un jeu multiplateforme pour Android, iOS et Windows à l’aide des Outils Visual Studio pour Unity

 Visual Studio Tools pour Unity est une extension gratuite de Visual Studio qui intègre l’édition de code performante de Visual Studio, la productivité et les outils de débogage avec *Unity*, un moteur de jeu/moteur graphique multiplateforme très répandu, qui est aussi un environnement de développement pour les applications immersives qui ciblent Windows, iOS, Android et d’autres plateformes, notamment le web.

 ![Environnement de développement VSTU](../cross-platform/media/vstu_overview.png "Présentation de Outils Visual Studio pour Unity")

 Avec Visual Studio Tools for Unity (VSTU), vous pouvez utiliser Visual Studio pour écrire des scripts d'éditeur et de jeu en C#, puis utiliser son débogueur performant pour rechercher et corriger les erreurs. La dernière version de VSTU prend en charge Unity 2018.1 et inclut la coloration syntaxique pour le langage du nuanceur ShaderLab d’Unity, une meilleure synchronisation avec Unity, un débogage plus performant et une amélioration de la génération du code pour l’Assistant MonoBehavior. VSTU apporte également vos fichiers de projet Unity et vos messages de console, et offre la possibilité de démarrer votre jeu dans Visual Studio, afin de perdre moins de temps à aller et venir de l’éditeur Unity en cours d’écriture.

|**En savoir plus**|
|--------------------|
|[En savoir plus sur la création de jeux Unity avec Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[En savoir plus sur les Outils Visual Studio pour Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md) |
|[Commencer à utiliser les Outils Visual Studio pour Unity](/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity.md) |
|[En savoir plus sur les dernières améliorations apportées à Visual Studio Tools for Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog de Visual Studio)|
|[Regarder une vidéo de présentation de Visual Studio Tools for Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) (vidéo)|
|[En savoir plus sur Unity](https://unity.com/) (site web Unity)|

## <a name="see-also"></a>Voir aussi

- [Ajouter des API Microsoft 365 à un projet Visual Studio](/office/developer-program/office-365-developer-program)
- [Azure App Services - Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
