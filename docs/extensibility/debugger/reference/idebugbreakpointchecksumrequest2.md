---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugBreakpointChecksumRequest2"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente une somme de contrôle document pour une requête de point d'arrêt.  
  
## Syntaxe  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Implémentée par le package de débogage de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] et consommé par les moteurs de débogage.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugBreakpointChecksumRequest2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Extrait la somme de contrôle document pour une requête de point d'arrêt données ID unique de l'algorithme de checksum à utiliser.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|détermine si la somme de contrôle est activée pour ce document.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll