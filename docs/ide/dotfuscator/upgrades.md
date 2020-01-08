---
title: Mettre à niveau Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, gratuit, Visual Studio 2019, Visual Studio 2017, Visual Studio, mise à niveau, ligne de commande
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Découvrez comment mettre à jour la copie gratuite de Dotfuscator Community fournie avec Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596799"
---
# <a name="upgrade-dotfuscator-community"></a>Mettre à niveau Dotfuscator Community

Dotfuscator Community offre instantanément de nombreuses fonctionnalités de durcissement et de protection des applications à tous les développeurs utilisant Microsoft Visual Studio.
Toutefois, les utilisateurs qui mettent à niveau leur version de Dotfuscator peuvent disposer de fonctionnalités supplémentaires.

## <a name="registering-dotfuscator-community"></a>Inscription de Dotfuscator Community

Les utilisateurs inscrits de Dotfuscator Community ont accès à des fonctionnalités supplémentaires, telles que la [prise en charge de ligne de commande][cli], ce qui facilite l’intégration de la communauté Dotfuscator à votre processus de génération automatisé. L’inscription accorde également l’accès à un outil intégré utilisé pour [décoder les traces de pile obscurcies][decode-obfuscated].

L’inscription est rapide, simple et gratuite.
Pour inscrire la communauté Dotfuscator, consultez [les instructions dans le guide complet de l’utilisateur de la communauté Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Alors que Dotfuscator Community fournit un niveau de protection de base, ***PreEmptive Protection - Dotfuscator, Professional*** inclut des transformations d’obfuscation et des fonctionnalités de protection avancées, comme :

* *Protection de la propriété intellectuelle*
  * Options de renommage supplémentaires, notamment la méthode Overload Induction™ améliorée et la sélection d’identificateur aléatoire.
  * Accès aux transformations d’obscurcissement au niveau de l’entreprise, y compris les [transformations ciblant la décompilation du code automatisé][control-flow].
  * La possibilité de [masquer des chaînes sensibles][string-encryption], ce qui rend impossible une recherche simple du code décompilé.
  * La possibilité d' [incorporer discrètement des chaînes de propriété et de distribution dans vos assemblys][watermarking], ce qui vous permet de déterminer la source de fuites logicielles non autorisées.
  * La possibilité de [combiner plusieurs assemblys en un seul][linking], ce qui rend encore plus difficile pour les attaquants de déterminer les rôles des éléments de code, car la séparation des préoccupations a été éliminée.
  * La possibilité de [supprimer automatiquement le code inutilisé de votre application][pruning], ce qui réduit la quantité de code sensible qui est livrée.
* *Protection de l’intégrité des applications*
  * Autres [comportements de protection des applications][check-actions].
  * La possibilité de fournir un délai d’avertissement avant l’échéance de fin de vie d’une application.
  * La possibilité de notifier le code d’application dans le délai d’avertissement de fin de vie ou après la date limite.

Dotfuscator Professional est le [brouilleur .net][net-obfuscator] standard, qui convient aux développeurs d’entreprise nécessitant un support continu, une maintenance et des mises à jour de produits.
De plus, Dotfuscator Professional offre une intégration à Visual Studio plus étroite et est concédé sous licence pour une utilisation commerciale.

Pour plus d’informations sur les fonctionnalités avancées de la protection des applications de Dotfuscator Professional, visitez la [page de présentation][product-about] de la solution PreEmptive Solutions et [Comparez-la à la communauté Dotfuscator][product-compare].
[Les versions d’évaluation entièrement prises en charge sont disponibles sur Preemptive.com][eval].

## <a name="see-also"></a>Voir aussi

[Cet article dans le guide complet de Dotfuscator Community User][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
