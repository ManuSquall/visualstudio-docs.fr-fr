---
title: Dotfuscator Community Edition (CE) | Microsoft Docs
ms.date: 2017-05-10
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Découvrez comment protéger vos applications .NET avec la version gratuite de Dotfuscator Community Edition incluse dans Visual Studio 2017."
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 507ff049dae50698d86e1536ed21ab982da1af85
ms.openlocfilehash: a4dd4e0f9a8f6c89452bc20e05139dfa5d062e0f
ms.contentlocale: fr-fr
ms.lasthandoff: 02/22/2017

---

# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* fournit une protection complète des applications .NET qui s’adapte facilement à votre cycle de vie de développement de logiciels sécurisé. Utilisez cet outil pour renforcer, protéger et nettoyer vos applications bureau, mobiles, serveur et intégrées afin de sécuriser les secrets industriels et autres droits de propriété intellectuelle (IP), réduire le piratage et la contrefaçon et vous protéger contre la falsification et le débogage non autorisé.
Dotfuscator fonctionne avec des assemblys compilés sans nécessiter de programmation supplémentaire ni même d’accès au code source.

![](media/header.svg)

## <a name="why-protection-matters"></a>Importance de la protection

Il est important de **protéger votre propriété intellectuelle** (IP).
Le code de votre application contient des informations de conception et d’implémentation qui peuvent être considérées comme une propriété intellectuelle.
Toutefois, les applications basées sur .NET Framework [contiennent des métadonnées importantes et un code intermédiaire de haut niveau][assemblies], ce qui les rend très vulnérables face à l’ingénierie inverse en utilisant simplement quelques outils automatisés gratuits.
En perturbant et en bloquant toute tentative d’ingénierie inverse, vous pouvez empêcher la divulgation non autorisée de votre propriété intellectuelle et montrer ainsi que votre code contient des secrets industriels.
Dotfuscator peut [masquer][obfuscation] vos assemblys .NET afin d’empêcher l’ingénierie inverse tout en conservant le comportement original de l’application.

Il est également important de **protéger l’intégrité de votre application**.
Outre l’ingénierie inverse, des personnes mal intentionnées peuvent chercher à pirater votre application, modifier son comportement lors de l’exécution, ou manipuler des données.
Dotfuscator s’intègre à votre application pour vous permettre de [détecter, signaler et répondre à des utilisations non autorisées][checks], notamment la falsification et le débogage par des tiers.

Pour plus d’informations sur l’intégration de Dotfuscator dans un cycle de vie de développement de logiciels sécurisé, consultez la [page SDL App Protection][sdl-protection] de PreEmptive Solutions.

## <a name="about-dotfuscator-ce"></a>À propos de Dotfuscator CE

Votre copie de Microsoft Visual Studio 2017 inclut une licence gratuite pour ** *Protection PreEmptive - Dotfuscator* Community Edition**, également appelée Dotfuscator CE.
Pour obtenir des instructions sur l’installation de la version de Dotfuscator CE fournie avec Visual Studio 2017, consultez la [page d’installation][install].

Dotfuscator CE propose toute une gamme de services [de protection et de renforcement][software-protection] destinés aux développeurs, architectes et testeurs. Voici des exemples de [masquage .NET][obfuscation] et d’autres fonctionnalités de [protection d’application][app-protection] incluses dans Dotfuscator CE :

* *[Changement du nom][renaming]* des identificateurs afin de compliquer l’ingénierie inverse des assemblys compilés.
* *[Anti-effraction][tamper]* pour détecter l’exécution des applications falsifiées, transmettre des alertes d’incident et fermer les sessions falsifiées.
* *[Anti-débogage][debug]* pour détecter la connexion d’un débogueur à une application en cours d’exécution, transmettre des alertes d’incident et fermer les sessions déboguées.
* *[Comportements d’expiration des applications][shelflife]* pour coder la date de « fin de vie », transmettre des alertes lorsque des applications sont exécutées après leur date d’expiration et fermer les sessions d’application qui ont expiré.
* *[Suivi des exceptions][exceptions]* pour surveiller les exceptions non gérées qui se produisent dans l’application.
* *[Suivi de l’utilisation des sessions][sessions] et des [fonctionnalités ][features]*pour identifier les applications qui ont été exécutées, dans quelles versions et pendant combien de temps.

Pour plus d’informations sur ces fonctionnalités, y compris leur intégration dans votre stratégie de protection des applications, consultez la [page sur les fonctionnalités][capabilities].

Dotfuscator CE offre une protection de base prête à l’emploi.
D’autres mesures de protection d’application sont disponibles pour les utilisateurs de Dotfuscator CE enregistrés et les utilisateurs de *PreEmptive Protection - Dotfuscator* Professional Edition, le [logiciel de masquage .NET][net-obfuscator] leader dans le monde.
Pour plus d’informations sur l’amélioration de Dotfuscator, reportez-vous à la [page des mises à niveau][upgrades].

## <a name="getting-started"></a>Commencer

Pour commencer à utiliser Dotfuscator CE depuis Visual Studio, tapez `dotfuscator` dans la barre de recherche **Lancement rapide** (Ctrl+Q).

* Si Dotfuscator CE est déjà installé, l’option *Menu* apparaît et vous permet de démarrer l’interface utilisateur de Dotfuscator CE. Pour plus d’informations, consultez [la page de prise en main du guide complet de Dotfuscator CE][get-started].
* Si Dotfuscator CE n’est pas encore installé, l’option *Installer* correspondante s’affiche. Consultez la [page d’installation][install] pour plus d’informations.

Vous pouvez également obtenir la **dernière version** de Dotfuscator CE sur [la page des téléchargements de Dotfuscator du site preemptive.com][download].

## <a name="full-documentation"></a>Documentation complète

Cette page et ses sous-pages fournissent une vue d’ensemble des fonctionnalités de Dotfuscator CE, ainsi que des [instructions d’installation de l’outil][install].

Consultez le [guide complet de l’utilisateur de Dotfuscator CE sur le site preemptive.com][full] pour obtenir des instructions d’utilisation détaillées, notamment [la prise en main de l’interface utilisateur de Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/articles/standard/assembly-format
[software-protection]: https://www.preemptive.com/software-protection
[obfuscation]: https://www.preemptive.com/obfuscation
[app-protection]: https://www.preemptive.com/application-protection
[sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[download]: https://www.preemptive.com/products/dotfuscator/downloads

[install]: install.md
[capabilities]: capabilities.md
[upgrades]: upgrades.md

[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/gui_getstarted.html

[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_renaming.html

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_shelflife.html

[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_features.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/index.html

