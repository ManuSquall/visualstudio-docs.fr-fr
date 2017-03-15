---
title: "Juste-&#224;-temps, D&#233;bogage, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.JIT"
  - "vs.debug.options.JIT"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Débogage juste-à-temps, définition des options"
  - "Options (boîte de dialogue), débogage"
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Juste-&#224;-temps, D&#233;bogage, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour accéder à la page **Juste\-à\-temps**, cliquez dans le menu **Outils** sur **Options**.  Dans la boîte de dialogue **Options**, développez le nœud **Débogage** et sélectionnez **Juste\-à\-temps**.  Cette page vous permet d'activer le débogage juste\-à\-temps pour le code managé, le code natif et les scripts.  Pour plus d'informations, consultez [Débogage juste\-à\-temps](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Vous pouvez activer le débogage juste\-à\-temps pour les types de programmes suivants :  
  
-   Managed  
  
-   Natif  
  
-   Script  
  
 Le débogage juste\-à\-temps est une technique pour le débogage d'un programme démarré à l'extérieur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il est possible d'exécuter un programme créé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en dehors de l'environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si vous avez activé le débogage juste\-à\-temps, un incident affichera une boîte de dialogue qui vous demandera si vous souhaitez déboguer.  
  
## Avertissements associés  
 Lorsque vous visitez cette page de la boîte de dialogue **Options**, vous pouvez découvrir un message d'avertissement tel que :  
  
 **Un autre débogueur s'est inscrit en tant que débogueur juste\-à\-temps.  Pour réparer, activez le débogage juste\-à\-temps ou exécutez la réparation de Visual Studio.**  
  
 Ce message se produit si vous avez un autre débogueur \(éventuellement une version antérieure du débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\) défini comme débogueur Juste\-à\-temps.  
  
 Voici un autre message que vous pouvez voir :  
  
 **Erreurs d'inscription de débogage juste\-à\-temps détectées.  Pour réparer, activez le débogage juste\-à\-temps ou exécutez la réparation de Visual Studio.**  
  
 En présence de l'un ou l'autre de ces avertissements, le débogage Juste\-à\-temps avec [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nécessite des droits d'administrateur jusqu'à ce que vous ayez résolu le problème.  Si vous essayez de poursuivre sans disposer de droits d'administrateur dans ces conditions, vous voyez s'afficher le message d'erreur suivant :  
  
 **Accès refusé.  Faites activer le débogage juste\-à\-temps par un administrateur ou réparez votre installation de Visual Studio.**  
  
## Voir aussi  
 [Débogage, boîte de dialogue Options](../debugger/debugging-options-dialog-box.md)   
 [Comment : spécifier les paramètres du débogueur](../debugger/how-to-specify-debugger-settings.md)