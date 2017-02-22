---
title: "Arr&#234;t et d&#233;tachement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmes, les événements d'arrêt"
  - "moteurs de débogage, le détachement de programmes"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Arr&#234;t et d&#233;tachement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent l'arrêt normal.  
  
## Discussion  
 Après [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) l'interface continue, s'il n'y a aucune point d'arrêt, exception, erreur d'exécution, ou boucle infinie dans l'application à déboguer, le programme débogué s'exécutera à l'achèvement.  Il s'agit d'arrêt normal.  
  
 vous devez envoyer [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter l'arrêt normal.  Cela nécessite implémentation de la méthode d' [IDebugProgramDestroyEvent2 : : GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) .  
  
## Voir aussi  
 [Création d'un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)