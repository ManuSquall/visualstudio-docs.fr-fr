---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, gratuit, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Découvrez comment protéger vos applications .NET avec la copie gratuite de Dotfuscator Community incluse dans Visual Studio.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 75437af41cec6fd770af9dfcdb399ed51543b7ff
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308218"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator*** fournit une protection complète des applications .NET qui s’adapte facilement à votre cycle de vie de développement de logiciels sécurisé.
Utilisez cet outil pour renforcer, protéger et nettoyer vos applications bureau, mobiles, serveur et intégrées afin de sécuriser les secrets industriels et autres droits de propriété intellectuelle (IP), réduire le piratage et la contrefaçon et vous protéger contre la falsification et le débogage non autorisé.
Dotfuscator fonctionne avec des assemblys compilés sans nécessiter de programmation supplémentaire ni même d’accès au code source.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Importance de la protection

Il est important de **protéger votre propriété intellectuelle** (IP).
Le code de votre application contient des informations de conception et d’implémentation qui peuvent être considérées comme une propriété intellectuelle.
Toutefois, les applications basées sur le .NET Framework [contiennent des métadonnées importantes et un code intermédiaire de haut niveau][assemblies], ce qui les rend vulnérables face à l’ingénierie inverse en utilisant simplement quelques outils automatisés gratuits.
En perturbant et en bloquant toute tentative d’ingénierie inverse, vous pouvez empêcher la divulgation non autorisée de votre propriété intellectuelle et montrer ainsi que votre code contient des secrets industriels.
Dotfuscator peut [obfusquer][obfuscation] vos assemblys .NET afin d’empêcher l’ingénierie inverse tout en conservant le comportement original de l’application.

Il est également important de **protéger l’intégrité de votre application**.
En plus de l’ingénierie inverse, des personnes mal intentionnées peuvent chercher à pirater votre application, modifier son comportement lors de l’exécution ou manipuler les données.
Dotfuscator s’intègre à votre application pour vous permettre de [détecter et répondre à des utilisations non autorisées][checks], notamment la falsification, le débogage par des tiers et les appareils rootés.

Pour plus d’informations sur l’intégration de Dotfuscator dans un cycle de vie de développement de logiciels sécurisé, consultez la [page SDL App Protection][sdl-protection] de PreEmptive Solutions.

## <a name="about-dotfuscator-community"></a>À propos de Dotfuscator Community

Votre copie de Microsoft Visual Studio inclut une copie de ***PreEmptive Protection - Dotfuscator Community***, dont vous pouvez profiter gratuitement pour un usage personnel.
(Cette version gratuite était connue sous le nom de Dotfuscator Community Edition ou Dotfuscator CE.) Pour des instructions sur l’installation de la version de Dotfuscator Community fournie avec Visual Studio, consultez la [page d’installation][install].

Dotfuscator Community propose toute une gamme de services de [protection et de durcissement][software-protection] destinés aux développeurs, architectes et testeurs.
Voici des exemples d’[obfuscation .NET][obfuscation] et d’autres fonctionnalités de [protection d’application][app-protection] incluses dans Dotfuscator Community :

* *[Renommage][renaming]* des identificateurs afin de compliquer l’ingénierie inverse des assemblys compilés.
* *[Anti-effraction][tamper]* pour détecter l’exécution des applications falsifiées et fermer ou répondre aux sessions falsifiées.
* *[Anti-débogage][debug]* pour détecter l’attachement d’un débogueur à une application en cours d’exécution et fermer ou répondre aux sessions déboguées.
* *[Appareil anti-rooté][root]* pour détecter si l’application s’exécute sur un appareil Android rooté et fermer ou répondre aux sessions sur ces appareils.
* *[Comportements d’expiration des applications][shelflife]* qui codent la date de « fin de vie » et ferment les sessions d’application qui ont expiré.

Pour plus d’informations sur ces fonctionnalités, notamment leur intégration dans votre stratégie de protection des applications, consultez la [page sur les fonctionnalités][capabilities].

Dotfuscator Community offre une protection de base prête à l’emploi.
D’autres mesures de protection d’application sont disponibles pour les utilisateurs inscrits de Dotfuscator Community et les utilisateurs de ***PreEmptive Protection - Dotfuscator Professional***, l’[obfuscateur .NET][net-obfuscator] leader mondial.
Pour plus d’informations sur l’amélioration de Dotfuscator, consultez la [page des mises à niveau][upgrades].

## <a name="getting-started"></a>Bien démarrer

::: moniker range=">=vs-2019"

Pour commencer à utiliser Dotfuscator Community depuis Visual Studio, tapez `dotfuscator` dans la **Zone de recherche** (Ctrl+Q).

* Si Dotfuscator Community est déjà installé, la **Zone de recherche** affiche l’option de démarrage de Dotfuscator Community sous le titre *Menus*. Pour des détails, consultez la [page de démarrage du guide complet de l’utilisateur de Dotfuscator Community][get-started].
* Si Dotfuscator Community n’est pas encore installé, la **Zone de recherche** affiche à la place **Installer PreEmptive Protection - Dotfuscator** sous le titre *Composants individuels*. Consultez la [page d’installation][install] pour plus d’informations.

::: moniker-end

::: moniker range="vs-2017"

Pour commencer à utiliser Dotfuscator Community depuis Visual Studio, tapez `dotfuscator` dans la barre de recherche **Lancement rapide** (Ctrl+Q).

* Si Dotfuscator Community est déjà installé, le **Lancement rapide** fait apparaître l’option *Menu* pour démarrer l’interface utilisateur de Dotfuscator Community. Pour des détails, consultez la [page de démarrage du guide complet de l’utilisateur de Dotfuscator Community][get-started].
* Si Dotfuscator Community n’est pas encore installé, le **Lancement rapide** fait apparaître l’option *Installer* appropriée. Consultez la [page d’installation][install] pour plus d’informations.

::: moniker-end

Vous pouvez également obtenir la **dernière version** de Dotfuscator Community dans [la page des téléchargements de Dotfuscator sur preemptive.com][download].

## <a name="full-documentation"></a>Documentation complète

Cette page et ses sous-pages fournissent une vue d’ensemble générale des fonctionnalités de Dotfuscator Community, ainsi que des [instructions d’installation de l’outil][install].

Consultez le [guide de l’utilisateur de Dotfuscator Community sur preemptive.com][full] pour obtenir des instructions d’utilisation détaillées, notamment [comment commencer à utiliser l’interface utilisateur de Dotfuscator Community][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
