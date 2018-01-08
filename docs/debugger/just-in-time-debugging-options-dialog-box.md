---
title: "Juste-à-temps, débogage, boîte de dialogue des Options | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
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
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 057c5e0e37d8e84daa4348c91847a12b6a9ae5e9
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Juste-à-temps, Débogage, boîte de dialogue Options
Pour accéder à la **juste-à-temps** page, accédez à la **outils** menu et cliquez sur **Options**. Dans le **Options** boîte de dialogue, développez le **débogage** nœud et sélectionnez **juste-à-temps**. Cette page vous permet d'activer le débogage juste-à-temps pour le code managé, le code natif et les scripts. Pour plus d’informations, consultez [débogage](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Vous pouvez activer le débogage juste-à-temps pour les types de programmes suivants :  
  
-   Managé  
  
-   Natif  
  
-   Script  
  
 Le débogage juste-à-temps est une technique pour le débogage d'un programme démarré à l'extérieur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il est possible d'exécuter un programme créé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en dehors de l'environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si vous avez activé le débogage juste-à-temps, un incident affichera une boîte de dialogue qui vous demandera si vous souhaitez déboguer.  
  
## <a name="associated-warnings"></a>Avertissements associés  
 Lorsque vous visitez cette page de la **Options** boîte de dialogue, vous pouvez voir un message d’avertissement comme suit :  
  
 **Un autre débogueur s’est inscrit comme juste-à-temps débogueur. Pour réparer, activez juste-à-temps de débogage ou exécutez la réparation de Visual Studio.**  
  
 Ce message se produit si vous avez un autre débogueur (éventuellement une version antérieure du débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]) défini comme débogueur Juste-à-temps.  
  
 Voici un autre message que vous pouvez voir :  
  
 **Erreurs d’inscription de débogage juste-à-temps détectées. Pour réparer, activez juste-à-temps de débogage ou exécutez la réparation de Visual Studio.**  
  
 Si vous voyez un de ces avertissements, avec le débogage juste-à-temps [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nécessite des privilèges d’administrateur jusqu'à ce que vous avez résolu le problème. Si vous essayez de poursuivre sans disposer de droits d'administrateur dans ces conditions, vous voyez s'afficher le message d'erreur suivant :  
  
 **L’accès est refusé. Possédant un administrateur de débogage activation juste-à-temps ou réparez votre installation de Visual Studio.**  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage, boîte de dialogue Options](../debugger/debugging-options-dialog-box.md)   
 [Guide pratique pour spécifier les paramètres du débogueur](../debugger/how-to-specify-debugger-settings.md)