---
title: En savoir plus sur le développement mobile avec Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.prod: xamarin
ms.technology: xamarin-tools
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 921faa49690b641fda0e864d27705040a1b97f1e
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454387"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>En savoir plus sur le développement pour appareils mobiles avec Xamarin

Cet article répertorie plusieurs vues d’ensemble qui peuvent vous aider à comprendre le développement d’applications mobiles multiplateformes avec Xamarin. Si vous n’avez pas encore installé Visual Studio et Xamarin, commencez d’abord le processus [Configurer et installer](../cross-platform/setup-and-install.md) , puis revenez ici pour consulter ces ressources pendant l’exécutant des programmes d’installation.  
  
> [!NOTE]
> Sauf mention contraire, vous pouvez d’abord lire seulement les pages qui sont ici en lien direct, et non les pages accessibles indirectement. Si le processus d’installation est en cours d’exécution une fois que vous avez terminé cette liste, n’hésitez pas à revenir en arrière et à explorer d’autres rubriques.  
>   
> N’hésitez pas non plus à consulter les rubriques « Notions de base » et à revenir ultérieurement dans les rubriques « Approfondissement ».  
  
## <a name="essentials-introduction-to-xamarin"></a>Notions de base : introduction à Xamarin  

*10 à 20 minutes*  
  
1.  [Applications mobiles dans Visual Studio avec Xamarin](https://www.visualstudio.com/xamarin/) (visualstudio.com) fournit un récapitulatif des principales caractéristiques de Xamarin.  
  
2.  [Building Cross-Platform Mobile Apps using C# and Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15 minutes et 16 secondes) avec l’expert Xamarin James Montemagno. Les trois premières minutes sont une vue d’ensemble de Xamarin, suivie de démonstrations de code.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Notions de base : vue d’ensemble de l’environnement Visual Studio et Xamarin  

*5 à 15 minutes*  
  
-   Vous effectuerez la plupart de votre travail sur l’ordinateur Windows disposant de Visual Studio et Xamarin. Sur cet ordinateur, vous générez directement des applications Windows et Android, que vous exécutez et déboguez sur le bureau, un appareil ou un émulateur. Vous pouvez aussi générer, exécuter et déboguer à distance des applications iOS via le Mac. Visual Studio sur l’ordinateur Windows peut également se connecter au concepteur de storyboard iOS et au simulateur iOS.  
  
-   Le Mac sur lequel Xcode et Visual Studio pour Mac sont installés sert d’hôte de build/signature et d’environnement d’exécution pour les applications iOS. L’ordinateur Windows délègue les builds iOS à ce Mac. L’application s’exécute dans un simulateur iOS sur le Mac ou directement sur un appareil attaché connecté au Mac. Vous pouvez interagir avec l’application sur le Mac, mais vous effectuez le débogage dans Visual Studio.
  
Ces relations sont illustrées ci-dessous.  
  
![Relation entre les ordinateurs de développement Windows et Mac dans un environnement Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  

> [!NOTE]
> L’appareil Windows Phone est représenté dans ce diagramme par souci d’exhaustivité. Quand vous utilisez la plateforme Xamarin, l’option de partage de code recommandée est une bibliothèque .NET Standard 2.0, qui est incompatible avec les appareils Windows Phone ou Windows 10 Mobile. 

Pour en savoir plus sur l’utilisation des applications iOS, consultez [Introduction à Xamarin.iOS pour Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).
  
## <a name="essentials-how-projects-are-structured"></a>Notions de base : structure des projets  

*10 à 30 minutes*  
  
1.  [Options de partage de code](/xamarin/cross-platform/app-fundamentals/code-sharing/). Pour les nouvelles applications, vous devez utiliser une bibliothèque .NET Standard pour partager du code. La plupart du code représentant la logique métier se trouvera dans la bibliothèque .NET Standard, notamment l’accès aux bases de données, les appels aux API REST et les appels aux composants Xamarin portables. (Consultez [Approfondissement : composants Xamarin](#components) à la fin de cet article.) Le code commun de l’interface utilisateur écrit avec Xamarin.Forms se trouve également dans une bibliothèque .NET Standard.  
  
2.  (Facultatif) [L’étude de cas Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) décrit certaines bonnes pratiques pour la conception et la structure d’une application complète. Elle explique notamment comment structurer le projet avec du code partagé qui sépare les données, l’accès aux données et les couches métier.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Notions de base : couches d’interface utilisateur natives et de Xamarin.Forms  

*10 à 40 minutes*  
  
Xamarin propose deux méthodes pour créer des applications réussies : Xamarin Native et Xamarin.Forms.  
  
Avec Xamarin Native, vous pouvez écrire du code d’interface utilisateur distinct pour chaque plateforme cible : iOS, Android et Windows.  Cette méthode fournit un accès direct aux API spécifiques à une plateforme afin de concevoir une expérience d’interface utilisateur personnalisée pour chaque plateforme.  Elle fournit également un accès complet au concepteur et aux commandes natifs de chaque plateforme pour faciliter la création de l’interface utilisateur correspondante.  
  
Xamarin.Forms contient un ensemble d’API généralisé qui vous permet d’écrire une couche d’interface utilisateur partagée pour toutes les plateformes dans une bibliothèque .NET Standard.  Xamarin.Forms effectue le rendu via des commandes natives sur chaque plateforme cible pour donner aux applications une apparence native.  Vous générez votre interface utilisateur avec C# et XAML au lieu d’utiliser un concepteur.  

La plupart des développeurs utilisent Xamarin.Forms. Il s’agit de la méthode recommandée pour les développeurs qui découvrent Xamarin. L’approche Xamarin Native est plus difficile et nécessite des connaissances plus détaillées sur les plateformes cibles.
  
Vous n’avez pas besoin de choisir entre les méthodes Xamarin Native et Xamarin.Forms, car vous pouvez implémenter des applications en utilisant une combinaison des deux :  
  
-   Utilisez Xamarin.Forms pour créer des écrans à usage général. Ceux-ci fournissent une interface utilisateur et des fonctionnalités similaires sur plusieurs plateformes, par exemple pour les connexions, les formulaires de contact et les résultats de recherche.  
  
-   Utilisez les diverses fonctionnalités de personnalisation dans Xamarin.Forms pour adapter l’interface utilisateur à chaque plateforme. L’option de personnalisation la plus simple implique l’API `OnPlatform`. Vous pouvez également créer des vues personnalisées, étendre les renderers existants et créer des renderers personnalisés.  
  
-   Si nécessaire, utilisez Xamarin Native pour créer des écrans qui utilisent des fonctionnalités uniques de l’interface utilisateur de chaque plateforme, par exemple un écran qui utilise la manipulation d’images et la capture vidéo natives.  
  
Vous devez généralement commencer par une solution Xamarin.Forms pour configurer le partage de code de l’interface utilisateur entre plateformes. Utilisez les fonctionnalités de personnalisation pour procéder ensuite à des réglages spécifiques à la plateforme. Si vous avez besoin de créer des écrans totalement distincts pour une plateforme, ajoutez-les individuellement à l’aide de Xamarin Native.  
  
Pour en savoir plus :  
  
1.  [Xamarin.Forms](/xamarin/xamarin-forms/) fournit une vue d’ensemble ainsi que les avantages et les inconvénients de Xamarin.Forms par rapport aux couches d’interfaces utilisateur natives (c’est-à-dire Xamarin.iOS et Xamarin.Android).  
  
2.  Les trois premières minutes de la vidéo de James Montemagno [Xamarin.Forms: Native iOS, Android & Windows apps with C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 minutes et 3 secondes) donnent une autre vue d’ensemble. Vous pouvez continuer à la regarder pour des démonstrations.  
  
3.  (Facultatif) [Introduction à Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (Facultatif) Consultez des exemples d’utilisation de l’API `OnPlatform` pour la personnalisation dans la documentation [Classe d’appareil](/xamarin/xamarin-forms/platform/device/).
  
5.  (Facultatif) L’article [Cross-Platform - Share UI Code Across Mobile Platforms with Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) de Jason Smith (MSDN Magazine) présente les différentes options de personnalisation disponibles dans Xamarin.Forms. L’utilisation de ces options est décrite en détail dans [Renderers personnalisés](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Approfondissement : déboguer à l’aide d’émulateurs  

*10 à 15 minutes*  
  
Pour déboguer vos applications multiplateformes sans avoir à utiliser d’appareil physique, vous devez utiliser les émulateurs décrits ici :  
  
### <a name="microsofts-android-emulator"></a>Émulateur Android de Microsoft 

Il est recommandé d’utiliser [l’émulateur Visual Studio pour Android](visual-studio-emulator-for-android.md) de Microsoft, qui est installé avec Visual Studio.  La vidéo sur l’ [émulateur Visual Studio pour Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel9, 5 minutes et 55 secondes) donne une vue d’ensemble de l’émulateur et montre comment l’utiliser.  
  
### <a name="apples-ios-simulator"></a>Simulateur iOS d’Apple

Pour en savoir plus, consultez [Getting Started with the iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
### <a name="microsofts-windows-phone-emulator"></a>Émulateur Windows Phone de Microsoft.

Pour en savoir plus, consultez [Test avec l’émulateur Microsoft pour Windows 10 Mobile](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/).  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Deeper Dive: Xamarin Components  

*10 minutes*  
  
De nombreuses capacités étendues sont disponibles pour les applications Xamarin via les composants Xamarin. Vous pouvez trouver le catalogue complet disponible en téléchargement sur [http://components.xamarin.com/](http://components.xamarin.com/), qui inclut des composants pour d’autres contrôles d’interface utilisateur, pour l’authentification, pour divers services cloud comme Microsoft Azure, et bien plus encore.