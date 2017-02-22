---
title: "IDebugPortSupplierEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPortSupplierEx2"
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fournit la prise en charge d'un fournisseur de port pour sélectionner et interagir avec un principal serveur.  
  
## Syntaxe  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface afin de pouvoir sélectionner le principal serveur à utiliser.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes **d'IDebugPortSupplierEx2**.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|définit le principal serveur pour le fournisseur de port.|  
  
## Configuration requise  
 en\-tête : Portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)