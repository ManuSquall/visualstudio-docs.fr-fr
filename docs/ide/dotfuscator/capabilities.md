---
title: Fonctionnalités de Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, gratuit, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Découvrez les fonctionnalités de la copie gratuite de Dotfuscator Community qui est fournie avec Visual Studio.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918403"
---
# <a name="capabilities-of-dotfuscator"></a>Fonctionnalités de Dotfuscator

Cette page se concentre sur les fonctionnalités de Dotfuscator Community et fait référence à certaines des options avancées disponibles via les [mises à niveau][upgrades].

Dotfuscator Community est un système *postbuild* pour les applications .NET.
Avec lui, les utilisateurs de Visual Studio peuvent [obfusquer les assemblys][obfuscation] et [injecter des mesures de défense actives][checks] dans l’application sans que Dotfuscator n’ait à accéder au code source d’origine.
Dotfuscator protège votre application de plusieurs façons, en créant une stratégie de protection multicouche.

Dotfuscator Community prend en charge de nombreux types d’applications et d’assemblys .NET, y compris [Universal Windows Platform (UWP)][uwp] et [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protection de la propriété intellectuelle

La conception, le comportement et l’implémentation de votre application sont des formes de propriété intellectuelle.
Cela dit, les applications créées pour .NET sont très simples à comprendre. En effet, il est facile d’appliquer une ingénierie à rebours sur les assemblys .NET, [car ils contiennent des métadonnées générales et du code intermédiaire][assemblies].

Dotfuscator Community comprend une fonctionnalité d’[obfuscation .NET][obfuscation] de base, qui prend la forme du [renommage][renaming].
L’obfuscation de votre code avec Dotfuscator permet de réduire les risques d’accès non autorisé au code source via l’ingénierie à rebours, car les informations de noms importantes ne sont plus publiques.
L’obfuscation montre également votre intention de protéger votre code de toute analyse, et participe à prouver que votre propriété intellectuelle est protégée juridiquement comme un secret commercial.

La plupart des [fonctionnalités de protection de l’intégrité des applications](#application-integrity-protection) qui sont disponibles dans Dotfuscator Communityempêchent l’ingénierie à rebours.
Par exemple, un acteur peut essayer d’attacher un débogueur à une instance en cours d’exécution de votre application afin de comprendre la logique du programme.
Pour empêcher cela, Dotfuscator peut injecter un [comportement anti-débogage][debug] dans votre application.

## <a name="application-integrity-protection"></a>Protection de l’intégrité des applications

En plus de protéger votre code source, il est important de s’assurer que votre application est bien utilisée comme prévu.
Des attaquants peuvent tenter de détourner votre application afin de contourner les stratégies de licences (piratage de logiciels), de voler ou de manipuler des données sensibles gérées par l’application, ou de modifier son comportement.

Dotfuscator Community peut injecter du [code de validation d’application][checks] dans vos assemblys, notamment des mesures [antifalsification][tamper], [antidébogage][debug] et [antiappareils rootés][root].
Lorsqu’un état d’application non valide est détecté, le code de validation peut [appeler du code d’application pour résoudre le problème de façon appropriée][check-app].
Si vous ne souhaitez pas écrire du code pour prendre en charge les utilisations non valides de l’application, Dotfuscator peut également injecter des comportements de [réponse][check-action], sans qu’il soit nécessaire d’apporter des modifications à votre code source.

La plupart de ces méthodes peuvent également être utilisées pour appliquer des [délais de fin de vie][shelflife] à des versions d’essai de logiciels.

## <a name="see-also"></a>Voir aussi

[Cette rubrique dans le guide complet de l’utilisateur de Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
