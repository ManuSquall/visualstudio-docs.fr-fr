---
title: En savoir plus sur le développement mobile avec Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: a362bd4eef2a48667c67c03e940e213fc960418b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919001"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>En savoir plus sur le développement pour appareils mobiles avec Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique vous dirige vers des supports de présentation qui vous permettent de comprendre le développement d’applications mobiles multiplateformes avec Xamarin. Si vous n’avez pas encore installé Visual Studio et Xamarin, commencez d’abord le processus [Setup and install](../cross-platform/setup-and-install.md) , puis revenez ici pour consulter ces ressources pendant l’exécutant des programmes d’installation.  
  
> [!NOTE]
> Sauf mention contraire, nous vous suggérons de lire d’abord seulement les pages qui sont ici en lien direct, et non pas des pages accessibles indirectement. Si le processus d’installation est en cours d’exécution une fois que vous avez terminé cette liste, n’hésitez pas à revenir en arrière et à explorer d’autres rubriques.  
>   
> N’hésitez pas non plus à consulter les rubriques « Notions de base » et à revenir ultérieurement dans les rubriques « Approfondissement ».  
  
## <a name="essentials-introduction-to-xamarin"></a>Notions de base : introduction à Xamarin  
 *10 à 20 minutes*  
  
1. [Applications mobiles dans Visual Studio avec Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) fournit un récapitulatif des principales caractéristiques de Xamarin.  
  
2. [Building Cross-Platform Mobile Apps using C# and Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15 minutes et 16 secondes) avec l’expert Xamarin James Montemagno. Les trois premières minutes sont une vue d’ensemble de Xamarin, suivie de démonstrations de code.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Notions de base : vue d’ensemble de l’environnement Visual Studio et Xamarin  
 *5 à 15 minutes*  
  
- Vous effectuerez la plupart de votre travail sur l’ordinateur Windows disposant de Visual Studio et Xamarin. Sur cet ordinateur, vous générez directement des applications Windows et Android, que vous exécutez et déboguez sur un appareil ou un émulateur. Vous générez, vous exécutez et vous déboguez aussi à distance des applications iOS via le Mac. Visual Studio sur l’ordinateur Windows peut également se connecter au concepteur de storyboard iOS et au simulateur iOS.  
  
- Le Mac avec Xcode et Xamarin sert d’hôte de build/signature et d’environnement d’exécution pour les applications iOS. Les builds pour iOS provenant de Visual Studio sur l’ordinateur Windows sont déléguées à ce Mac. Quand vous déboguez une application iOS depuis Visual Studio, elle s’exécute dans le simulateur iOS sur le Mac ou directement sur un appareil attaché connecté au Mac. Dans ce cas, vous allez interagir avec l’application sur ou à proximité du Mac, et vous allez effectuer le débogage dans Visual Studio.  
  
  Ces relations sont illustrées ci-dessous. Pour en savoir plus sur l’utilisation des applications iOS, consultez [Introduction to Xamarin.iOS for Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (xamarin.com).  
  
  ![Relation entre les ordinateurs de développement Windows et Mac dans un environnement Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin en savoir plus 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Notions de base : structure des projets  
 *10 à 30 minutes*  
  
1. [Sharing Code Options](/xamarin/cross-platform/app-fundamentals/code-sharing) (xamarin.com). Nous recommandons d’utiliser l’option de bibliothèques de classes portables, car elle offre une meilleure prise en charge de l’utilisation des seules API .NET qui sont prises en charge sur toutes les plateformes cibles. La plupart du code représentant la logique métier se trouve dans la bibliothèque de classes portables, notamment l’accès aux bases de données, les appels aux API REST et les appels aux composants Xamarin portables (pour plus d’informations, consultez [Deeper Dive: Xamarin Components](#components) , à la fin de cette rubrique). Le code commun de l’interface utilisateur écrit avec Xamarin.Forms peut également se trouver dans une bibliothèque de classes portables.  
  
2. (Facultatif) L’ [étude de cas Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (xamarin.com) décrit quelques-unes des meilleures pratiques pour la conception et la structure d’une application complète. Elle explique notamment comment structurer le projet avec une PCL pour le code partagé qui sépare les données, l’accès aux données et les couches métier.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Notions de base : couches d’interface utilisateur natives et de Xamarin.Forms  
 *10 à 40 minutes*  
  
 Xamarin propose deux méthodes pour créer des applications natives : Xamarin Native et Xamarin.Forms.  
  
 Avec Xamarin Native, vous pouvez écrire du code d’interface utilisateur distinct pour chaque plateforme cible : iOS, Android et Windows.  Cette méthode fournit un accès direct aux API spécifiques à une plateforme, ce qui vous permet d’offrir une expérience d’interface utilisateur personnalisée pour chaque plateforme.  Elle fournit également un accès complet au concepteur et aux commandes natifs de chaque plateforme pour faciliter la création de l’interface utilisateur correspondante.  
  
 Xamarin.Forms contient un ensemble d’API généralisé qui vous permet d’écrire une couche d’interface utilisateur partagée pour toutes les plateformes dans une bibliothèque de classes portables.  Xamarin.Forms effectue le rendu via des commandes natives sur chaque plateforme cible pour donner aux applications une apparence native.  Avec Xamarin.Forms, vous générez votre interface utilisateur avec C# et XAML au lieu d’utiliser un concepteur.  
  
 Vous n’avez pas besoin de choisir entre les méthodes Xamarin Native et Xamarin.Forms, car vous pouvez implémenter des applications en utilisant une combinaison des deux :  
  
- Utilisez Xamarin.Forms pour créer des écrans à usage général qui fournissent une interface utilisateur et des fonctionnalités similaires sur plusieurs plateformes, par exemple pour les connexions, les formulaires de contact et les résultats de recherche.  
  
- Utilisez les diverses fonctionnalités de personnalisation dans Xamarin.Forms pour adapter l’interface utilisateur à chaque plateforme. Cela inclut l’API OnPlatform qui peut être utilisée à partir du code et de XAML, la création d’un affichage personnalisé, l’extension d’un convertisseur existant et la création d’un convertisseur personnalisé.  
  
- Choisissez Xamarin Native si vous devez créer des écrans qui utilisent des fonctionnalités uniques de l’interface utilisateur de chaque plateforme, par exemple un écran qui utilise la manipulation d’images et la capture vidéo natives.  
  
  Nous vous recommandons de toujours commencer avec une solution Xamarin.Forms pour créer le code de l’interface utilisateur partagé entre les différentes plateformes, puis d’utiliser les fonctions de personnalisation pour effectuer les ajustements propres à chaque plateforme. Si vous avez besoin de créer des écrans totalement distincts pour une plateforme, ajoutez-les individuellement à l’aide de Xamarin Native.  
  
  Pour en savoir plus :  
  
1. [Xamarin.Forms](/xamarin/xamarin-forms/) (xamarin.com) fournit une vue d’ensemble ainsi que les avantages et les inconvénients de Xamarin.Forms par rapport aux couches d’interfaces utilisateur natives (c’est-à-dire Xamarin.iOS et Xamarin.Android).  
  
2. Les trois premières minutes de la vidéo de James Montemagno [Xamarin.Forms: Native iOS, Android & Windows apps with C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 minutes et 3 secondes) donnent une autre vue d’ensemble. Vous pouvez continuer à la regarder pour des démonstrations.  
  
3. (Facultatif) [An Introduction to Xamarin.Forms](/xamarin/get-started/quickstarts/deepdive?pivots=windows) (xamarin.com)  
  
4. (Facultatif) Consultez des exemples d’utilisation de l’API OnPlatform pour la personnalisation dans [Device Class](/xamarin/xamarin-forms/platform/device) (xamarin.com).  
  
5. (Facultatif) L’article [Cross-Platform - Share UI Code Across Mobile Platforms with Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) de Jason Smith (MSDN Magazine) présente les différentes options de personnalisation disponibles dans Xamarin.Forms. L’utilisation de ces options est décrite en détail dans [Customizing Controls on Each Platform](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Approfondissement : déboguer à l’aide d’émulateurs  
 *10 à 15 minutes*  
  
 Pour déboguer vos applications multiplateformes sans avoir à utiliser d’appareil physique, vous avez besoin des éléments suivants :  
  
1. **Émulateur Android.** Selon votre version de Windows, nous vous recommandons d’utiliser l’émulateur Visual Studio pour Android de Microsoft ou l’émulateur de Xamarin. Ces deux émulateurs sont performants et prennent en charge un large éventail de fonctionnalités d’appareil :  
  
    - **Machines avec Windows 8 ou version ultérieure** : nous vous recommandons fortement d’utiliser l’ [émulateur Visual Studio pour Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx)de Microsoft, qui est installé avec Visual Studio.  L' [émulateur Visual Studio pour Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) Video (channel9, 55 secondes) donne une vue d’ensemble et une démonstration.  
  
    - **Windows 7 ou version antérieure sur Mac OS X**: utilisez le lecteur [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
  
2. **Simulateur iOS d’Apple.** .  Pour en savoir plus, consultez [Getting Started with the iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3. **Émulateur de Windows Phone de Microsoft.** Pour en savoir plus, consultez [Émulateur Windows Phone pour Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
## <a name="deeper-dive-xamarin-components"></a><a name="components"></a> Approfondissement : composants Xamarin  
 *10 minutes*  
  
 De nombreuses capacités étendues sont disponibles pour les applications Xamarin via les composants Xamarin. Vous pouvez trouver le catalogue complet disponible en téléchargement sur [http://components.xamarin.com/](/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows) , qui comprend des composants pour d’autres contrôles d’interface utilisateur, l’authentification, une variété de services Cloud tels que Microsoft Azure, et bien plus encore.
