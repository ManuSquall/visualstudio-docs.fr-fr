---
title: Xamarin
description: 'L’utilisation de Xamarin dans Visual Studio pour Mac vous permet de créer des applications multiplateformes ciblant iOS, Mac, Android, tvOS et watchOS '
author: conceptdev
ms.author: crdun
ms.date: 02/12/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.openlocfilehash: 7d9cfbcafc90340d15172dd0d862ef9904fd6715
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73716115"
---
# <a name="xamarin-mobile-app-development"></a>Développement d’applications mobiles Xamarin

La prise en charge poussée de [Xamarin](/xamarin) permet de développer des expériences natives riches pour Android, macOS, iOS, tvOS et watchOS. Les applications multiplateformes Xamarin.Forms permettent de partager le code d’interface utilisateur XAML entre Android, iOS et macOS sans limiter l’accès aux fonctionnalités natives.

## <a name="android"></a>Android

Visual Studio pour Mac dispose de son propre gestionnaire Android SDK intégré, ce qui vous permet d’accéder aux kits SDK que doit cibler votre application.

Pour les applications Android, Visual Studio pour Mac inclut son propre concepteur, qui fonctionne avec des fichiers `.axml` Android pour créer visuellement des interfaces utilisateur. Visual Studio pour Mac ouvre ces fichiers dans Android Designer, comme illustré dans l’image suivante :

![Concepteur d’interface utilisateur Android](media/intro-image31.png)

Pour plus d’informations sur Android Designer, consultez le guide de [présentation de Xamarin.Android Designer](/xamarin/android/user-interface/android-designer/index).

## <a name="ios"></a>iOS

Le concepteur iOS est entièrement intégré à Visual Studio pour Mac et permet la modification visuelle des fichiers .xib et Storyboard pour créer des interfaces utilisateur et des transitions iOS, tvOS et WatchOS. L’interface utilisateur toute entière peut être créée à l’aide de la fonctionnalité de glisser-déplacer entre la boîte à outils et l’aire de conception, tout en utilisant une approche intuitive pour la gestion des événements. Le concepteur iOS prend également en charge les [contrôles personnalisés](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) avec l’avantage supplémentaire du rendu au moment du design.

![Concepteur de Storyboard iOS](media/intro-image30.png)

Pour plus d’informations sur l’utilisation du concepteur iOS, consultez les guides du [concepteur](/xamarin/ios/user-interface/designer/?tabs=macos).

### <a name="mac"></a>Mac

Xamarin fournit des liaisons d’API Mac natives, qui vous permettent de créer de belles applications Mac.

Pour plus d’informations sur l’écriture d’applications Mac avec Visual Studio pour Mac, consultez les guides [Xamarin.Mac](/xamarin/mac/get-started/index).

## <a name="xamarin-enterprise-features"></a>Fonctionnalités de Xamarin Enterprise

> [!Note]
> Ces produits peuvent être utilisés seulement avec un abonnement Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler a trois instruments disponibles pour le profilage. Le guide [Introduction to the Xamarin Profiler](/xamarin/tools/profiler/index?tabs=macos) explore ce que ces instruments mesurent et comment ils analysent votre application, et explique la signification des données présentées sur chaque écran.

### <a name="inspector"></a>Inspector

Xamarin Inspector fournit une console C# interactive avec des outils utilisateur. Il peut être utilisé comme aide au débogage ou au diagnostic lors de l’inspection des applications dynamiques, comme outil d’apprentissage, comme outil de documentation ou comme outil d’expérimentation.

![Xamarin Inspector](media/intro-inspector.png)

Il consiste en une application autonome qui fournit une console C# enrichie, qui peut cibler différentes plateformes de programmation (Android, iOS, Mac et Windows) et s’intégrer au flux de travail de débogage de vos IDE.

Pour plus d’informations, consultez le guide [Xamarin Inspector](/xamarin/tools/inspector/).