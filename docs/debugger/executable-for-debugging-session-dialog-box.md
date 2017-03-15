---
title: "Ex&#233;cutable pour la session de d&#233;bogage, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "fichiers exécutables, spécification lors du débogage"
  - "DLL, débogage"
  - "débogueur, boîte de dialogue Exécutable pour la session de débogage"
  - "Exécutable pour la session de débogage (boîte de dialogue)"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ex&#233;cutable pour la session de d&#233;bogage, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié.  Visual Studio ne peut pas lancer une DLL directement.  Il lance d'abord l'exécutable spécifié.  Vous pouvez déboguer la DLL après l'avoir appelée dans l'exécutable.  
  
 **Nom de fichier de l'exécutable**  
 Entrez le chemin d'accès d'un exécutable qui appelle la DLL à déboguer.  
  
 **URL d'accès au projet \(ATL Server uniquement\)**  
 Si vous déboguez une DLL ATL Server, entrez l'URL permettant d'accéder au projet.  
  
 Les paramètres que vous entrez sont stockés dans les Pages de propriétés du projet, de sorte que vous n'avez pas à les entrer à nouveau lors des sessions de débogage suivantes.  Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus.  Pour plus d'informations sur la spécification d'un exécutable pour la session de débogage, consultez [Débogage de DLL](../Topic/How%20to:%20Debug%20Native%20DLLs.md).  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)