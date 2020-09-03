---
title: Juste-à-temps, débogage, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201105"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Juste-à-temps, Débogage, boîte de dialogue Options
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour accéder à la page **Juste-à-temps**, dans le menu **Outils**, cliquez sur **Options**. Dans la boîte de dialogue **Options**, développez le nœud **Débogage** et sélectionnez **Juste-à-temps**. Cette page vous permet d'activer le débogage juste-à-temps pour le code managé, le code natif et les scripts. Pour plus d’informations, consultez [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Vous pouvez activer le débogage juste-à-temps pour les types de programmes suivants :  
  
- Géré  
  
- Natif  
  
- Script  
  
  Le débogage juste-à-temps est une technique pour le débogage d'un programme démarré à l'extérieur de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il est possible d'exécuter un programme créé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en dehors de l'environnement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si vous avez activé le débogage juste-à-temps, un incident affichera une boîte de dialogue qui vous demandera si vous souhaitez déboguer.  
  
## <a name="associated-warnings"></a>Avertissements associés  
 Quand vous visitez cette page de la boîte de dialogue **Options**, vous pouvez découvrir un message d’avertissement tel que :  
  
 **Un autre débogueur s’est inscrit en tant que débogueur juste-à-temps. Pour réparer, activez le débogage juste-à-temps ou exécutez la réparation de Visual Studio.**  
  
 Ce message se produit si vous avez un autre débogueur (éventuellement une version antérieure du débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) défini comme débogueur Juste-à-temps.  
  
 Voici un autre message que vous pouvez voir :  
  
 **Erreurs d’inscription de débogage juste-à-temps détectées. Pour réparer, activez le débogage juste-à-temps ou exécutez la réparation de Visual Studio.**  
  
 En présence de l’un ou l’autre de ces avertissements, le débogage Juste-à-temps avec [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nécessite des droits d’administrateur jusqu’à ce que vous ayez résolu le problème. Si vous essayez de poursuivre sans disposer de droits d'administrateur dans ces conditions, vous voyez s'afficher le message d'erreur suivant :  
  
 **L’accès est refusé. Demander à un administrateur d’activer le débogage juste-à-temps, ou de réparer votre installation de Visual Studio.**  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage, boîte de dialogue Options](../debugger/debugging-options-dialog-box.md)   
 [Comment : spécifier les paramètres du débogueur](../debugger/how-to-specify-debugger-settings.md)
