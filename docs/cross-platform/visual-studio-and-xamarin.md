---
title: Visual Studio et Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 30bc5e4d14e09852904ca93087bdd99f6f2443ef
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280687"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio et Xamarin

Xamarin est une plateforme de développement d’applications mobiles pour la création d’applications iOS, Android et Windows natives à partir d’une base de code C#/.NET commune. Les applications écrites avec Xamarin permettent de réutiliser de 75 à presque 100 % du code entre les plateformes. Ces applications ont un accès complet aux API de la plateforme sous-jacente et peuvent incorporer des interfaces utilisateur natives. Elles compilent des packages spécifiques aux plateformes avec peu d’impact sur les performances d’exécution. (Remarque : Xamarin prend également en charge F#, mais cette documentation se concentre uniquement sur C#. Visual Basic n’est pas pris en charge pour le moment.)

Les développeurs familiarisés avec C#, .NET et Visual Studio vont bénéficier des mêmes puissance et productivité quand ils utilisent Xamarin pour des applications mobiles. Ces avantages incluent le débogage à distance sur les appareils Android, iOS et Windows, sans devoir apprendre les langages de codage natifs comme Objective-C ou Java. Il n’est donc pas étonnant que de nombreuses applications très performantes avec de belles interfaces utilisateur, comme NASCAR, Aviva et MixRadio, aient été créées avec Xamarin.

Cette documentation vous permet d’évaluer toute la puissance de **Visual Studio avec Xamarin** pour créer ces expériences utilisateur.

-   Commencez par ceci : [Configurer et installer](../cross-platform/setup-and-install.md), un processus qui prend un certain temps (généralement de 2 à 4 heures, selon la vitesse de votre connexion web, vos installations précédentes et les options sélectionnées).

-   Pendant l’exécution des programmes d’installation, vous pouvez consulter [En savoir plus sur le développement mobile avec Xamarin](learn-about-mobile-development-with-xamarin.md). Vous y trouverez des informations sur la nature de Xamarin, vous pourrez comparer Xamarin.Forms à l’IU native, etc.

-   Une fois l’installation terminée, il est recommandé de [vérifier votre environnement Xamarin](../cross-platform/verify-your-xamarin-environment.md).

-   Pour finir, parcourez le didacticiel [Principes fondamentaux de la création d’applications avec Xamarin.Forms dans Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Vous pouvez utiliser toutes les fonctionnalités de Xamarin via [n’importe quelle édition de Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community, Professional et Enterprise). Aucune licence distincte n’est nécessaire.

> [!NOTE]
>  Ces instructions décrivent la configuration la plus simple et la plus directe de l’ordinateur pour les développeurs qui connaissent bien Windows et Visual Studio. Avec cette configuration, toute la pratique du développement est simplifiée, car vous devez seulement interagir avec le Mac pour utiliser le simulateur iOS et les appareils attachés. En revanche, si vous connaissez mieux l’univers Mac, nous vous recommandons d’exécuter Visual Studio dans Parallels ou VMWare, ou d’utiliser Visual Studio pour Mac. Pour obtenir des instructions, consultez [Configuration, installation et vérifications pour les utilisateurs Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).

> [!NOTE]
>  Si vous recherchez une solution de développement multiplateforme en HTML et CSS, consultez Visual Studio Tools pour Apache Cordova comme indiqué dans [Développement mobile multiplateforme dans Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).