---
title: Juste-à-temps, débogage, de boîte de dialogue Options | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5522c9da025b76a3892d3923cdd7397b8ed5ce5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207491"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Juste-à-temps, Débogage, boîte de dialogue Options
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour accéder à la **juste-à-temps** page, accédez à la **outils** menu et cliquez sur **Options**. Dans le **Options** boîte de dialogue, développez le **débogage** nœud et sélectionnez **juste-à-temps**. Cette page vous permet d'activer le débogage juste-à-temps pour le code managé, le code natif et les scripts. Pour plus d’informations, consultez [débogage juste à temps](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Vous pouvez activer le débogage juste-à-temps pour les types de programmes suivants :  
  
-   Managé  
  
-   Natif  
  
-   Script  
  
 Le débogage juste-à-temps est une technique pour le débogage d'un programme démarré à l'extérieur de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il est possible d'exécuter un programme créé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en dehors de l'environnement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si vous avez activé le débogage juste-à-temps, un incident affichera une boîte de dialogue qui vous demandera si vous souhaitez déboguer.  
  
## <a name="associated-warnings"></a>Avertissements associés  
 Lorsque vous visitez cette page de la **Options** boîte de dialogue, vous pouvez voir un message d’avertissement comme suit :  
  
 **Un autre débogueur s’est inscrit en tant que juste-à-temps débogueur. Pour réparer, activez juste-à-temps de débogage ou exécutez la réparation de Visual Studio.**  
  
 Ce message se produit si vous avez un autre débogueur (éventuellement une version antérieure du débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) défini comme débogueur Juste-à-temps.  
  
 Voici un autre message que vous pouvez voir :  
  
 **Erreurs d’inscription de débogage juste-à-temps détectées. Pour réparer, activez juste-à-temps de débogage ou exécutez la réparation de Visual Studio.**  
  
 Si vous voyez une de ces avertissements, avec le débogage juste-à-temps [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nécessite des privilèges d’administrateur jusqu'à ce que vous ayez résolu le problème. Si vous essayez de poursuivre sans disposer de droits d'administrateur dans ces conditions, vous voyez s'afficher le message d'erreur suivant :  
  
 **L’accès est refusé. Un administrateur activer juste-à-temps de débogage sont, ou réparer votre installation de Visual Studio.**  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage, boîte de dialogue Options](../debugger/debugging-options-dialog-box.md)   
 [Guide pratique pour spécifier les paramètres du débogueur](../debugger/how-to-specify-debugger-settings.md)



