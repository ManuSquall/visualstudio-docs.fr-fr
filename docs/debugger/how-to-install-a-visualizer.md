---
title: "Comment&#160;: installer un visualiseur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "débogueur, visualiseurs"
  - "visualiseurs, installer"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: installer un visualiseur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  L'installation d'un visualiseur est un processus simple.  
  
> [!NOTE]
>  Dans les applications de **Store**, seul les visualiseurs HTML, XML, JSON et de texte standard sont pris en charge.  Les visualiseurs personnalisés \(créés par l'utilisateur\) ne sont pas pris en charge.  
  
### Pour installer un visualiseur  
  
1.  Recherchez la DLL qui contient le visualiseur que vous avez créé.  
  
2.  Copiez la DLL dans l'un ou l'autre des emplacements suivants :  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d'accès sur l'ordinateur distant.  
  
4.  Redémarrez la session de débogage.  
  
## Voir aussi  
 [Visualiseurs](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)