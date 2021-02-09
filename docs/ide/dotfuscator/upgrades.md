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
manager: jmartens
ms.openlocfilehash: a0e3ad3e5f6afbd6675f8e65c918b4a5d7c66dd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922781"
---
# <a name="upgrade-dotfuscator-community"></a>Mettre à niveau Dotfuscator Community

Dotfuscator Community offre instantanément de nombreuses fonctionnalités de durcissement et de protection des applications à tous les développeurs utilisant Microsoft Visual Studio.
Toutefois, les utilisateurs qui mettent à niveau leur version de Dotfuscator peuvent disposer de fonctionnalités supplémentaires.

## <a name="registering-dotfuscator-community"></a>Inscription de Dotfuscator Community

Les utilisateurs de Dotfuscator Community inscrits peuvent accéder à des fonctionnalités supplémentaires, telles que la [prise en charge des lignes de commande][cli], ce qui permet d’intégrer facilement Dotfuscator Community au processus de génération automatisé. L’inscription donne également accès à un outil intégré employé pour le [décodage des traces de pile obfusquées][decode-obfuscated].

L’inscription est rapide, simple et gratuite.
Pour inscrire Dotfuscator Community, consultez [les instructions du Guide complet de l’utilisateur de Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Alors que Dotfuscator Community fournit un niveau de protection de base, ***PreEmptive Protection - Dotfuscator, Professional*** inclut des transformations d’obfuscation et des fonctionnalités de protection avancées, comme :

* *Protection de la propriété intellectuelle*
  * Options de renommage supplémentaires, notamment la méthode Overload Induction™ améliorée et la sélection d’identificateur aléatoire.
  * Accès aux transformations d’obfuscation de niveau entreprise, notamment les [transformations visant à mettre en échec la décompilation de code automatisée][control-flow].
  * La possibilité de [masquer des chaînes sensibles][string-encryption], ce qui rend impossible une recherche simple du code décompilé.
  * La possibilité [d’incorporer discrètement des chaînes de propriété et la distribution dans vos assemblys][watermarking], ce qui vous permet de déterminer la source des fuites logicielles non autorisées.
  * La possibilité de [regrouper plusieurs assemblys en un seul][linking], ce qui complique encore davantage la tâche des personnes malveillantes souhaitant déterminer les rôles des éléments de code puisque plus rien n’est séparé.
  * La possibilité de [supprimer automatiquement le code non utilisé de votre application][pruning], ce qui réduit la quantité de code sensible fourni.
* *Protection de l’intégrité des applications*
  * [Comportements de défense des applications][check-actions] supplémentaires.
  * La possibilité de fournir un délai d’avertissement avant l’échéance de fin de vie d’une application.
  * La possibilité de notifier le code d’application dans le délai d’avertissement de fin de vie ou après la date limite.

Dotfuscator Professional est l’[obfuscateur .NET][net-obfuscator] standard. Il est approprié pour les développeurs d’entreprise nécessitant un support technique, une maintenance et des mises à jour de produits continus.
De plus, Dotfuscator Professional offre une intégration à Visual Studio plus étroite et est concédé sous licence pour une utilisation commerciale.

Pour plus d’informations sur les fonctionnalités de protection des applications avancées de Dotfuscator Professional, visitez la [page de présentation de Dotfuscator][product-about] de PreEmptive Solutions et [comparez-le à Dotfuscator Community][product-compare].
[Des essais entièrement pris en charge sont disponibles sur le site preemptive.com][eval].

## <a name="see-also"></a>Voir aussi

[Cet article dans le guide complet de l’utilisateur de Dotfuscator Community][full]

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
