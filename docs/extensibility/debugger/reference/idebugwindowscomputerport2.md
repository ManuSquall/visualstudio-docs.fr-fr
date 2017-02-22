---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugWindowsComputerPort2"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permet demander des informations sur l'ordinateur cible.  
  
## Syntaxe  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les objets de port du gestionnaire de débogage de session.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugWindowsComputerPort2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Récupère des informations relatives à l'ordinateur sur lequel le débogueur en cours de exécution.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll