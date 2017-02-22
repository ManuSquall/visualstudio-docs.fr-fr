---
title: "Modules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modules"
  - "débogage [Debugging SDK], modules"
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Modules
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quant à l'architecture du débogueur, **un module**:  
  
-   Est un conteneur physique de code, tel qu'un fichier exécutable ou une DLL.  
  
-   peut recharger ses symboles et se décrire.  Les descriptions de module sont affichées dans la fenêtre modules de l'IDE.  
  
-   Est représenté par une interface d' [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , créée par un moteur de débogage pour décrire le module.  
  
## Voir aussi  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)