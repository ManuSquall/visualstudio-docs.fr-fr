---
title: "Proc&#233;dure&#160;: s&#233;rialiser les informations de symboles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "outils de profilage, sérialiser les informations de symboles"
  - "outils d’analyse des performances, sérialiser les informations de symboles"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Proc&#233;dure&#160;: s&#233;rialiser les informations de symboles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez sérialiser les symboles nécessaires à l'analyse de votre application.  La sérialisation de symboles ajoute des symboles au fichier .vsp.  En ajoutant des informations de symboles au fichier .vsp, d'autres peuvent analyser le rapport de performances sans devoir accéder aux symboles d'origine.  Si les symboles ne sont pas sérialisés, vous aurez besoin des fichiers.exe et .pdb instrumentés d'origine pour analyser le fichier .vsp.  
  
### Pour sérialiser automatiquement les informations de symboles  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
     La boîte de dialogue **Options** s'affiche.  
  
2.  Cliquez sur **Outils d'analyse des performances**.  
  
3.  Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/fr-fr/0340ddde-caf4-48ac-8af3-d15dcdade556)