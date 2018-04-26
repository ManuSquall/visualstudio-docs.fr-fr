---
title: Fonctionnalités de Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Découvrez les fonctionnalités de la version gratuite de Dotfuscator Community Edition qui est fournie avec Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: 39ec170858074cb7cb2bc4ab580cb2268164e0ad
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="capabilities-of-dotfuscator"></a>Fonctionnalités de Dotfuscator

Cette page se concentre sur les fonctionnalités de Dotfuscator Community Edition (Dotfuscator CE) et fait référence à certaines des options avancées disponibles via les [mises à niveau][upgrades].

Dotfuscator est un système *post-build* pour applications .NET.
Avec Dotfuscator CE, les utilisateurs de Visual Studio peuvent [obfusquer les assemblys][obfuscation], mais aussi injecter une [défense active][checks] et un [suivi analytique][analytics] dans l’application et ce, sans que Dotfuscator n’ait à accéder au code source d’origine.
Dotfuscator protège votre application de plusieurs façons, en créant une stratégie de protection multicouche.

Dotfuscator CE prend en charge de nombreux types d’applications et d’assemblys .NET, y compris [Universal Windows Platform (UWP)][uwp] et [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protection de la propriété intellectuelle

La conception, le comportement et l’implémentation de votre application sont des formes de propriété intellectuelle.
Cela dit, les applications créées pour le .NET Framework sont très simples à comprendre. En effet, il est très facile d’appliquer une ingénierie à rebours sur les assemblys .NET, [car ils contiennent des métadonnées générales et du code intermédiaire][assemblies].

Dotfuscator CE comprend une fonctionnalité d’[obfuscation .NET][obfuscation] de base, qui prend la forme du [renommage][renaming].
L’obfuscation de votre code avec Dotfuscator permet de réduire les risques d’accès non autorisé au code source via l’ingénierie à rebours, car les informations de noms importantes ne sont plus publiques.
L’obfuscation montre également votre intention de protéger votre code de toute analyse, et participe à prouver que votre propriété intellectuelle est protégée juridiquement comme un secret commercial.

La plupart des [fonctionnalités de protection de l’intégrité des applications](#application-integrity-protection) qui sont disponibles dans Dotfuscator empêchent l’ingénierie à rebours.
Par exemple, un acteur peut essayer d’attacher un débogueur à une instance en cours d’exécution de votre application afin de comprendre la logique du programme.
Pour empêcher cela, Dotfuscator peut injecter un [comportement anti-débogage][debug] dans votre application.

## <a name="application-integrity-protection"></a>Protection de l’intégrité des applications

En plus de protéger votre code source, il est important de s’assurer que votre application est bien utilisée comme prévu.
Des pirates peuvent tenter de détourner votre application afin de contourner les stratégies de licences (piratage de logiciels), de voler ou de manipuler des données sensibles gérées par l’application, ou de modifier le comportement de l’application.

Dotfuscator CE peut injecter du [code de validation d’application][checks] dans vos assemblys, notamment des mesures [anti-violation][tamper] et des mesures [anti-débogage][debug].
Lorsqu’un état d’application non valide est détecté, le code de validation peut [appeler du code d’application pour résoudre le problème de façon appropriée][check-app].
Si vous ne voulez pas écrire de code pour gérer les utilisations non valides de l’application, Dotfuscator peut également injecter des comportements de [rapport de télémétrie][check-telemetry] et de [réponse][check-action], sans nécessiter de modifications de votre code source.

La plupart de ces méthodes peuvent également être utilisées pour appliquer des [délais de fin de vie][shelflife] à des versions d’essai de logiciels.

## <a name="application-monitoring"></a>Analyse d'applications

Lorsque vous développez une application, il est essentiel de comprendre les modèles de comportement des utilisateurs, notamment des bêta-testeurs et des utilisateurs de versions antérieures.
L’analyse des applications permet d’effectuer le suivi de la fréquence et du type d’utilisation des applications, y compris les erreurs auxquelles sont confrontés les utilisateurs.

Dotfuscator CE peut injecter du code de [suivi des exceptions][exceptions], de [suivi des sessions][sessions] et de [suivi des fonctionnalités][features] dans votre application.
Lorsqu’elle est exécutée, l’application traitée transmet les données d’analyse à un [point de terminaison PreEmptive Analytics][endpoints] configuré.

## <a name="see-also"></a>Voir aussi

[Cette rubrique dans le guide d’utilisation complet de Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

- [assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
- [uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
- [xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

- [upgrades]: upgrades.md

- [obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
- [renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

- [analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html
- [endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html#endpoints

- [checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
- [check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
- [check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

- [tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
- [debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
- [shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
- [exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
- [sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
- [features]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html
- [check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_checks.html

- [full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html