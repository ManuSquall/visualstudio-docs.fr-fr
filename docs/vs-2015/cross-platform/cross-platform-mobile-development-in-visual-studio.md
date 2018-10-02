---
title: Développement mobile multiplateforme dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 68ecf06ba6a2bdb40355ab645ea35774c8b73c09
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494723"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Développement mobile multiplateforme dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Cross-Platform Mobile Development dans Visual Studio](https://docs.microsoft.com/visualstudio/cross-platform/cross-platform-mobile-development-in-visual-studio).  
  
  
Vous pouvez créer des applications pour des appareils Android, iOS et Windows à l'aide de Visual Studio.  Quand vous concevez votre application, utilisez les outils de Visual Studio pour ajouter facilement des services connectés, comme Office 365, Azure App Service et Application Insights.  
  
 Créez vos applications en utilisant C# et le .NET Framework, HTML et JavaScript, ou C++. Partagez du code, des chaînes, des images et même, dans certains cas, l’interface utilisateur.  
  
 Si vous souhaitez créer un jeu ou une application graphique immersive, installez les Visual Studio Tools pour Unity et profitez de toutes les puissantes fonctionnalités de productivité de Visual Studio avec Unity, un moteur de jeu/moteur graphique multiplateforme très répandu, qui est aussi un environnement de développement pour les applications qui s’exécutent sur iOS, Android, Windows et d’autres plateformes.  
  
 **Dans cet article :**  
  
-   [Générer une application pour Android, iOS et Windows (.NET Framework)](#NET)  
  
    -   [Cibler Android, iOS et Windows à partir d’une seule base de code](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)  
  
    -   [Cibler les appareils Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)  
  
-   [Générer une application pour Android, iOS et Windows (HTML/JavaScript)](#HTML)  
  
-   [Générer une application pour Android et Windows (C++)](#CPP)  
  
-   [Créer un jeu multiplateforme pour Android, iOS et Windows à l’aide de Visual Studio Tools pour Unity](#Unity)  
  
##  <a name="NET"></a> Générer une application pour Android, iOS et Windows (.NET Framework)  
 ![Appareils](../cross-platform/media/homedevices.png "HomeDevices")  
  
 Avec Xamarin, vous pouvez cibler Windows, iOS et Android dans la même solution, partager du code et même l’interface utilisateur.  
  
|**En savoir plus**|  
|--------------------|  
|[Installer Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|  
|[En savoir plus sur Xamarin dans Visual Studio](http://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com)|  
|[Visual Studio et Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Library)|  
|[Application Lifecycle Management (ALM) avec les applications Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Library)|  
|[En savoir plus sur les applications Windows universelles dans Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|  
|[En savoir plus sur les similitudes entre Swift et C#](http://aka.ms/scposter) (download.microsoft.com)|  
|[En savoir plus sur l’émulateur Visual Studio pour Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|  
  
###  <a name="AndroidHTML"></a> Cibler Android, iOS et Windows à partir d’une seule base de code  
 Vous pouvez générer des applications natives pour Android, iOS et Windows en C# ou F# (Visual Basic n’est pas pris en charge pour le moment).  Pour commencer, installez Visual Studio 2015. Dans le programme d’installation, sélectionnez l’option **Personnalisé**, puis cochez la case sous **Développement multiplateforme pour appareils mobiles > C#/.NET (Xamarin)**. Vous pouvez également démarrer le [Programme d’installation Xamarin](https://www.xamarin.com/download), qui permet d’installer Xamarin pour Visual Studio 2013.  
  
 Si Visual Studio 2015 est déjà installé, exécutez le programme d’installation à partir de **Panneau de configuration > Programmes et fonctionnalités**, puis sélectionnez la même option **Personnalisé** pour Xamarin, comme indiqué ci-dessus.  
  
 Une fois que vous avez terminé, les modèles de projet s’affichent dans la boîte de dialogue **Nouveau projet**. La meilleure façon de trouver des modèles Xamarin consiste à effectuer simplement une recherche sur « Xamarin ».  
  
 Xamarin expose les fonctionnalités natives d’Android, d’iOS et de Windows en tant qu’objets .NET. Ainsi, vos applications ont un accès total aux API natives et aux contrôles utilisateur natifs. Elles sont tout aussi réactives que les applications écrites dans les langages de plateforme natifs.  
  
 Après avoir créé un projet, vous pourrez profiter de toutes les fonctionnalités de productivité de Visual Studio. Par exemple, vous allez utiliser un concepteur pour créer vos pages, et la fonctionnalité IntelliSense pour explorer les API natives des plateformes mobiles. Une fois que vous êtes prêt à exécuter votre application et à vérifier son fonctionnement, vous pouvez utiliser l’émulateur Visual Studio pour Android ou l’émulateur du kit SDK Android, exécuter les applications Windows en mode natif ou exécuter les applications Windows sur l’émulateur Windows Phone. Vous pouvez également utiliser directement des appareils Android et Windows attachés. Pour les projets iOS, connectez-vous à un Mac en réseau et démarrez l’émulateur Mac à partir de Visual Studio, ou connectez-vous à un appareil attaché.  
  
#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Concevoir un ensemble de pages qui s'affichent sur tous les appareils à l'aide de Xamarin.Forms  
 Selon la complexité de la conception de vos applications, vous pouvez envisager de les créer en utilisant les modèles *Xamarin.Forms* du groupe de modèles de projet **Applications mobiles** . Xamarin.Forms est un kit de ressources d’IU qui vous permet de créer une interface utilisateur que vous pouvez partager sur Android et iOS, ainsi que sur Windows Phone.  Quand vous compilez une solution Xamarin.Forms, vous obtenez une application Android, une application iOS et une application Windows. Pour plus d’informations, consultez [En savoir plus sur le développement mobile avec Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
####  <a name="ShareHTML"></a> Partager du code entre des applications Android, iOS et Windows  
 Si vous n'utilisez pas Xamarin.Forms et que vous choisissez de concevoir pour chaque plateforme individuellement, vous pouvez partager la plus grande partie du code autre que celui de l'interface utilisateur entre les projets des différentes plateformes (iOS, Android et Windows). Cela inclut la logique métier, l'intégration du cloud, l'accès aux bases de données ou tout autre code qui cible le .NET Framework. Le seul code que vous ne pouvez pas partager est le code qui cible une plateforme spécifique.  
  
 ![Partager du code entre les interfaces utilisateur Android, iOS et Windows](../cross-platform/media/sharecode.png "ShareCode")  
  
 Vous pouvez partager votre code en utilisant un projet partagé, un projet de bibliothèque de classes portables ou les deux. Vous trouverez peut-être qu'une partie du code est mieux placé dans un projet partagé, et que d'autres parties ont davantage de sens placées dans un projet de bibliothèque de classes portables.  
  
|**En savoir plus**|  
|--------------------|  
|Décidez si vous voulez partager votre code à l'aide de projets partagés, de projets de bibliothèque de classes portables ou les deux.<br /><br /> [Partage de code entre plateformes](http://blogs.msdn.com/b/dotnet/archive/2014/04/21/sharing-code-across-platforms.aspx) (blog de .NET Framework)<br /><br /> [Sharing Code Options](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Xamarin)<br /><br /> [Options de partage de code avec .NET Framework](http://msdn.microsoft.com/library/dn720832.aspx) (MSDN Library)|  
  
###  <a name="WindowsHTML"></a> Cibler les appareils Windows 10  
 ![Appareils Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")  
  
 Si vous voulez créer une application unique qui cible la totalité des appareils Windows 10, créez une application Windows universelle. Vous allez concevoir l'application à l'aide d'un seul projet, et vos pages s'afficheront correctement, quel que soit l'appareil utilisé pour les visualiser.  
  
 Démarrez avec un modèle de projet d'application Windows universelle. Concevez vos pages visuellement, puis ouvrez-les dans une fenêtre d'aperçu pour voir comment elles apparaissent sur les différents types d'appareils. Si vous n'aimez pas la façon dont une page apparaît sur un appareil, vous pouvez optimiser cette page pour qu'elle soit mieux adaptée à la taille d'écran, à la résolution ou aux différentes orientations, comme le mode paysage ou le mode portrait. Vous pouvez faire tout cela à l'aide des fenêtres d'un outil intuitif et des options de menu facilement accessibles dans Visual Studio. Quand vous êtes prêt à exécuter votre application et à avancer pas à pas dans votre code, vous avez à votre disposition tous les émulateurs et simulateurs pour différents types d'appareils dans une seule liste déroulante, qui se trouve sur la barre d'outils **Standard** .  
  
 Windows 10 étant relativement nouveau, vous trouverez également des modèles de projet qui ciblent Windows 8.1. Vous pouvez utiliser ces modèles de projet si vous le souhaitez : votre application s'exécutera sur les téléphones, les tablettes et les ordinateurs Windows 10. Cependant, tous les appareils exécutant Windows 8.1 recevront une mise à niveau automatique vers Windows 10. Par conséquent, sauf si vous avez des raisons spécifiques de cibler plutôt Windows 8.1, nous vous recommandons d'utiliser les modèles de projet qui ciblent Windows 10.  
  
|**En savoir plus**|  
|--------------------|  
|[En savoir plus sur les applications Windows universelles](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Centre de développement Windows)|  
|[Créer votre première application](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Centre de développement Windows)|  
|[Développer des applications pour la plateforme Windows universelle (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|  
|[Migrer des applications vers la plateforme Windows universelle (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|  
  
##  <a name="HTML"></a> Générer une application pour Android, iOS et Windows (HTML/JavaScript)  
 ![Appareils](../cross-platform/media/homedevices.png "HomeDevices")  
  
 Si vous êtes un développeur web et si vous connaissez bien les langages HTML et JavaScript, vous pouvez cibler Windows, Android et iOS en utilisant Visual Studio Tools pour Apache Cordova. Ces applications peuvent cibler les trois plateformes et vous pouvez les créer en utilisant les compétences et les processus qui vous sont les plus familiers.  
  
 Apache Cordova est un framework qui inclut un modèle de plug-in. Ce modèle de plug-in fournit une seule API JavaScript qui vous permet d’accéder aux fonctionnalités natives des appareils des trois plateformes (Android, iOS et Windows).  
  
 Étant donné que ces API sont multiplateformes, vous pouvez partager la plus grande partie de ce que vous écrivez entre les trois plateformes. Ceci permet de réduire les coûts de développement et de maintenance. En outre, vous ne devez pas démarrer de rien. Si vous avez créé d'autres types d'applications web, vous pouvez partager ces fichiers avec votre application Cordova sans avoir à les modifier ou à les reconcevoir d'une quelconque façon.  
  
 ![Multi&#45;Device Hybrid Apps](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")  
  
 Pour commencer, installez Visual Studio 2015 et choisissez la fonctionnalité **HTML/JavaScript (Apache Cordova)** au cours de l'installation. Si vous utilisez Visual Studio 2013, installez l’extension Visual Studio Tools pour Apache Cordova. Dans tous les cas, cette extension installe automatiquement l’ensemble des logiciels tiers nécessaires pour générer votre application multiplateforme.  
  
 Une fois que vous avez installé l'extension, ouvrez Visual Studio et créez un projet **Application vide (Apache Cordova)** . Ensuite, vous pouvez développer votre application en utilisant JavaScript ou TypeScript. Vous pouvez aussi ajouter des plug-ins pour étendre les fonctionnalités de votre application. Les API des plug-ins s'affichent alors dans IntelliSense quand vous écrivez du code.  
  
 Quand vous êtes prêt à exécuter votre application et votre code pas à pas, choisissez un émulateur, par exemple l’émulateur Apache Ripple ou l’émulateur Visual Studio (Android ou Windows Phone), un navigateur ou un appareil que vous avez connecté directement à votre ordinateur. Ensuite, démarrez votre application. Si vous développez votre application sur un ordinateur Windows, vous pouvez même l'exécuter sur cet ordinateur. Toutes ces options sont intégrées à Visual Studio via Visual Studio Tools pour Apache Cordova.  
  
 Les modèles de projet pour créer des applications Windows universelles sont toujours disponibles dans Visual Studio donc n'hésitez pas à les utiliser si vous envisagez de cibler uniquement des appareils Windows. Si vous décidez plus tard de cibler Android et iOS, vous pouvez toujours porter votre code vers un projet Cordova. Il existe des versions open source des API WinJS. Vous pouvez donc réutiliser tout code utilisant ces API. Ceci dit, si vous envisagez de cibler d'autres plateformes à l'avenir, nous vous recommandons de commencer avec Visual Studio Tools pour Apache Cordova.  
  
|**En savoir plus**|  
|--------------------|  
|[Installer Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|  
|[Prise en main de Visual Studio Tools pour Apache Cordova](http://taco.visualstudio.com/en-us/docs/get-started-vs-tools-apache-cordova/) (taco.visualstudio.com)|  
|[En savoir plus sur l’émulateur Visual Studio pour Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|  
  
##  <a name="CPP"></a> Générer une application pour Android et Windows (C++)  
 ![Utiliser C&#43;&#43; pour générer des applications pour Android, iOS, et Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")  
  
 Commencez par installer Visual Studio 2015 et les outils Visual C++ pour le développement mobile multiplateforme. Vous pouvez ensuite générer une application d’activité native pour Android ou une application qui cible Windows. Les modèles C++ qui ciblent iOS ne sont pas encore disponibles. Vous pouvez cibler Android et Windows dans la même solution si vous le souhaitez, puis partager le code entre eux à l’aide d’une bibliothèque partagée statique ou dynamique multiplateforme.  
  
 Si vous devez générer une application pour Android qui nécessite toute sorte de manipulations graphiques avancées (par exemple un jeu), vous pouvez le faire en C++. Commencez par le projet **Application Activité native (Android)** . Ce projet offre une prise en charge complète de la chaîne d'outils Clang.  
  
 ![Modèle de projet d’activité native](../cross-platform/media/cross-plat-cpp-native.png "Cross-Plat_CPP_Native")  
  
 Lorsque vous êtes prêt à exécuter et découvrir votre application, vous pouvez utiliser l'émulateur Visual Studio pour Android. Il est rapide, fiable, et facile à utiliser et à configurer.  
  
 Vous pouvez également créer une application qui cible la totalité des appareils Windows 10 en utilisant C++ et un modèle de projet d'application Windows universelle. Pour en savoir plus sur cette question, consultez la section [Cibler les appareils Windows 10](#WindowsHTML) plus haut dans cette rubrique.  
  
 Vous pouvez partager du code C++ entre Android et Windows en créant une bibliothèque partagée statique ou dynamique.  
  
 ![Bibliothèques partagées statiques et dynamiques](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")  
  
 Vous pouvez utiliser cette bibliothèque dans un projet Windows ou Android, tel que ceux décrits précédemment dans cette section. Vous pouvez également l'utiliser dans une application que vous créez à l'aide de Xamarin, Java ou n'importe quel langage qui vous permet d'appeler des fonctions dans une DLL non managée.  
  
 Lorsque vous écrivez le code dans ces bibliothèques, vous pouvez utiliser IntelliSense pour explorer les API natives des plateformes Android et Windows. Ces projets de bibliothèque sont entièrement intégrés au débogueur Visual Studio, de sorte que vous pouvez définir des points d'arrêt, parcourir le code, et rechercher et résoudre les problèmes à l'aide de toutes les fonctionnalités avancées du débogueur.  
  
|**En savoir plus**|  
|--------------------|  
|[Télécharger Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|  
|[Installer les outils Visual C++ pour le développement mobile multiplateforme](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|  
|[En savoir plus sur l’utilisation de C++ pour cibler plusieurs plateformes](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|  
|[Installer les éléments nécessaires et créer une application d’activité native pour Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|  
|[En savoir plus sur l’émulateur Visual Studio pour Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|  
|[En savoir plus sur le partage de code C++ avec les applications Android et Windows](http://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx) (VisualStudio.com)|  
|[Exemples de développement mobile multiplateforme pour C++](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Library)|  
|[Exemples supplémentaires de développement mobile multiplateforme pour C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|  
  
##  <a name="Unity"></a> Créer un jeu multiplateforme pour Android, iOS et Windows à l’aide de Visual Studio Tools pour Unity  
 Visual Studio Tools pour Unity est une extension gratuite de Visual Studio qui intègre l’édition de code performante de Visual Studio, la productivité et les outils de débogage avec *Unity*, un moteur de jeu/moteur graphique multiplateforme très répandu, qui est aussi un environnement de développement pour les applications immersives qui ciblent Windows, iOS, Android et d’autres plateformes, notamment le web.  
  
 ![Environnement de développement VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")  
  
 Avec Visual Studio Tools for Unity (VSTU), vous pouvez utiliser Visual Studio pour écrire des scripts d'éditeur et de jeu en C#, puis utiliser son débogueur performant pour rechercher et corriger les erreurs. La dernière version de VSTU prend en charge Unity 5 et inclut la coloration de syntaxe pour le langage du nuanceur ShaderLab d'Unity, une meilleure synchronisation avec Unity, un débogage plus avancé et une génération de code améliorée pour l'Assistant MonoBehavior. VSTU apporte également vos fichiers de projet Unity et vos messages de console, et offre la possibilité de démarrer votre jeu dans Visual Studio, afin de perdre moins de temps à aller et venir de l'éditeur Unity en cours d'écriture.  
  
 Commencez à créer votre jeu avec Unity et Visual Studio Tools for Unity dès aujourd'hui.  
  
|**En savoir plus**|  
|--------------------|  
|[En savoir plus sur la création de jeux Unity avec Visual Studio](https://www.visualstudio.com/en-us/features/unitytools-vs.aspx)|  
|[En savoir plus sur Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library)|  
|[Commencer à utiliser Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Library)|  
|[En savoir plus sur les dernières améliorations apportées à Visual Studio Tools for Unity 2.0 Preview](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (blog de Visual Studio)|  
|[Regarder une vidéo de présentation de Visual Studio Tools for Unity 2.0 Preview](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (vidéo)|  
|[En savoir plus sur Unity](http://unity3d.com/) (site web Unity)|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter les API Office 365 à un projet Visual Studio](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)   
 [Azure Mobile Services](http://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)   
 [Application Insights](../misc/application-insights-for-visual-studio-online.md)

