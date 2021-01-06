---
title: Juste-à-temps, débogage, boîte de dialogue Options | Microsoft Docs
description: Le débogage juste-à-temps vous permet de déboguer des programmes qui démarrent en dehors de Visual Studio. Découvrez comment activer le débogage juste-à-temps pour différents types de programmes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b346cfdae8671f8f647d41065d5793184fefd3fb
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903868"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Juste-à-temps, Débogage, boîte de dialogue Options
Pour accéder à la page **Juste-à-temps**, dans le menu **Outils**, cliquez sur **Options**. Dans la boîte de dialogue **Options**, développez le nœud **Débogage** et sélectionnez **Juste-à-temps**. Cette page vous permet d'activer le débogage juste-à-temps pour le code managé, le code natif et les scripts. Pour plus d’informations, consultez [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md).

 Vous pouvez activer le débogage juste-à-temps pour les types de programmes suivants :

- Géré

- Natif

- Script

  Le débogage juste-à-temps est une technique pour le débogage d'un programme démarré à l'extérieur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il est possible d'exécuter un programme créé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en dehors de l'environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si vous avez activé le débogage juste-à-temps, un incident affichera une boîte de dialogue qui vous demandera si vous souhaitez déboguer.

## <a name="associated-warnings"></a>Avertissements associés
 Quand vous visitez cette page de la boîte de dialogue **Options**, vous pouvez découvrir un message d’avertissement tel que :

 **Un autre débogueur s’est inscrit en tant que débogueur juste-à-temps. Pour réparer, activez le débogage juste-à-temps ou exécutez la réparation de Visual Studio.**

 Ce message se produit si vous avez un autre débogueur (éventuellement une version antérieure du débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]) défini comme débogueur Juste-à-temps.

 Voici un autre message que vous pouvez voir :

 **Erreurs d’inscription de débogage juste-à-temps détectées. Pour réparer, activez le débogage juste-à-temps ou exécutez la réparation de Visual Studio.**

 En présence de l’un ou l’autre de ces avertissements, le débogage Juste-à-temps avec [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nécessite des droits d’administrateur jusqu’à ce que vous ayez résolu le problème. Si vous essayez de poursuivre sans disposer de droits d'administrateur dans ces conditions, vous voyez s'afficher le message d'erreur suivant :

 **L’accès est refusé. Demander à un administrateur d’activer le débogage juste-à-temps, ou de réparer votre installation de Visual Studio.**

## <a name="see-also"></a>Voir aussi
- [Débogage, boîte de dialogue Options](../debugger/debugging-options-dialog-box.md)
- [Comment : spécifier les paramètres du débogueur](../debugger/how-to-specify-debugger-settings.md)