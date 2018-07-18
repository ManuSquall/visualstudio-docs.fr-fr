---
title: Présentation de Visual Studio pour Mac
description: Cet article présente les fonctionnalités de Visual Studio pour Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 31459717e9a2c001a9ae4f0efef5ebb0930af1c8
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693690"
---
# <a name="introducing-visual-studio-for-mac"></a>Présentation de Visual Studio pour Mac

Visual Studio pour Mac est un IDE moderne et élaboré avec de nombreuses fonctionnalités permettant de créer des applications mobiles, de poste de travail et web. Il prend en charge les types de développement suivants :

* Applications mobiles avec .NET : Android, iOS, tvOS, watchOS
* Applications de poste de travail pour Mac
* Applications .NET Core
* Applications web ASP.NET Core
* Jeux Unity multiplateformes

Il inclut des fonctionnalités comme un éditeur avancé, le débogage, l’intégration de plateforme native avec iOS, Mac et Android, et un contrôle du code source intégré.

Cet article traite de différents aspects de Visual Studio pour Mac et présente certaines des fonctionnalités qui en font un outil puissant pour créer des applications multiplateformes.

## <a name="installation"></a>Installation

Suivez les étapes du guide [Installation](installation.md) pour télécharger et installer Visual Studio pour Mac.

## <a name="language-support"></a>Langages pris en charge

Visual Studio pour Mac prend en charge par défaut le développement en C# et en F#.

### <a name="c"></a>C#

C# est le langage le plus couramment utilisé pour la création d’applications multiplateformes dans Visual Studio pour Mac. L’IDE prend entièrement en charge toutes les fonctionnalités de C# 7.

### <a name="f"></a>F#

F# est un langage de programmation fonctionnel fortement typé conçu pour s’exécuter sur .NET. Il est disponible comme langage de programmation pour les utilisateurs de Visual Studio pour Mac sur Android, Mac et iOS. Pour plus d’informations sur l’utilisation de F# et pour obtenir des exemples créés dans ce langage, consultez les guides [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/).

## <a name="platform-support"></a>Plateforme prise en charge

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) est une plateforme de création d’applications qui s’exécutent sur Windows, Linux et Mac. Visual Studio pour Mac prend en charge le chargement, la création, l’exécution et le débogage de projets .NET Core.

Pour exécuter des projets .NET Core, vous devez télécharger et installer le SDK .NET Core.

La prise en charge de .NET Core inclut :

* IntelliSense C# et F#.
* Modèles de projet .NET Core pour applications console, bibliothèque et web.
* Prise en charge complète du débogage, notamment des points d’arrêt, de la pile d’appels, de la fenêtre Espion, etc.
* NuGet PackageReferences et restauration MSBuild.
* Prise en charge intégrée des tests unitaires pour l’exécution et le débogage de tests avec la plateforme de test Visual Studio fournie avec le SDK .NET Core.
* Migration depuis l’ancien format project.json.

Pour commencer, découvrez les [ateliers pratiques](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) consacrés aux applications web ASP.NET Core.

## <a name="xamarin"></a>Xamarin

La prise en charge poussée de [Xamarin](https://developer.xamarin.com/) permet de développer des expériences natives riches pour Android, macOS, iOS, tvOS et watchOS. Les applications multiplateformes Xamarin.Forms permettent de partager le code d’interface utilisateur XAML entre Android, iOS et macOS sans limiter l’accès aux fonctionnalités natives.

Pour commencer, découvrez les [ateliers pratiques](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started) consacrés aux applications mobiles.

### <a name="android"></a>Android

Visual Studio a son propre gestionnaire intégré d’Android SDK.

Pour les applications Android, Visual Studio pour Mac inclut son propre concepteur, qui fonctionne avec des fichiers `.axml` Android pour créer visuellement des interfaces utilisateur. Visual Studio pour Mac ouvre ces fichiers dans Android Designer, comme illustré dans l’image suivante :

![Concepteur d’interface utilisateur Android](media/intro-image31.png)

Pour plus d’informations sur Android Designer, consultez le document [Designer Overview](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview).

### <a name="ios"></a>iOS

Le concepteur iOS est entièrement intégré à Visual Studio pour Mac et permet la modification visuelle des fichiers .xib et Storyboard pour créer des interfaces utilisateur et des transitions iOS, tvOS et WatchOS. L’interface utilisateur toute entière peut être créée à l’aide de la fonctionnalité de glisser-déplacer entre la boîte à outils et l’aire de conception, tout en utilisant une approche intuitive pour la gestion des événements. Le concepteur iOS prend également en charge les [contrôles personnalisés](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) avec l’avantage supplémentaire du rendu au moment du design.

![Concepteur de Storyboard iOS](media/intro-image30.png)

Pour plus d’informations sur l’utilisation du Designer iOS, reportez-vous aux documents sur le [Designer](https://developer.xamarin.com/guides/ios/user_interface/designer).

### <a name="mac"></a>Mac

Xamarin fournit des liaisons d’API Mac natives, qui vous permettent de créer de belles applications Mac.

Pour plus d’informations sur l’écriture d’applications Mac avec Visual Studio pour Mac, reportez-vous à la documentation de [Xamarin.Mac](https://developer.xamarin.com/guides/#mac).

## <a name="gaming"></a>Jeux

Visual Studio pour Mac prend en charge le développement de jeux multiplateformes avec Unity 5.6.1.

Pour commencer, découvrez les [ateliers pratiques](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started) consacrés à Unity.

## <a name="enterprise-features"></a>Fonctionnalités d’entreprise

> [!Note]
> Ces produits peuvent être utilisés seulement avec un abonnement Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler a trois instruments disponibles pour le profilage. Le guide [Introduction to the Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) explore ce que ces instruments mesurent et comment ils analysent votre application, et explique la signification des données présentées sur chaque écran.

### <a name="inspector"></a>Inspector

Xamarin Inspector fournit une console C# interactive avec des outils pour les utilisateurs. Il peut être utilisé comme aide au débogage ou au diagnostic lors de l’inspection des applications dynamiques, comme outil d’apprentissage, comme outil de documentation ou comme outil d’expérimentation.

![Xamarin Inspector](media/intro-inspector.png)

Il consiste en une application autonome qui fournit une console C# enrichie, qui peut cibler différentes plateformes de programmation (Android, iOS, Mac et Windows) et s’intégrer au flux de travail de débogage de votre IDE.

Pour plus d’informations, consultez le guide [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/).

## <a name="next-steps"></a>Étapes suivantes

* **Vue d’ensemble** : pour obtenir une vue d’ensemble d’un grand nombre des fonctionnalités principales de Visual Studio pour Mac, consultez la [visite guidée de l’IDE](ide-tour.md) de Visual Studio pour Mac.
* **Installation** : pour découvrir comment télécharger et installer Visual Studio, consultez le guide [Installation](installation.md).
* **Didacticiels Xamarin** - Pour en savoir plus sur la façon de développer du code avec Xamarin, accédez au [Developer Center](https://developer.xamarin.com) de Xamarin.
* **Vidéos** - Pour en savoir plus sur les autres fonctionnalités et aspects de Visual Studio pour Mac, regardez des vidéos sur le site web [Xamarin University](https://university.xamarin.com).
* **Ateliers pratiques** - Pour commencer à utiliser les différentes charges de travail incluses dans Visual Studio pour Mac, consultez les [ateliers pratiques](https://github.com/Microsoft/vs4mac-labs).
