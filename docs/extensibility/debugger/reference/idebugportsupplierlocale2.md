---
title: "IDebugPortSupplierLocale2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugPortSupplierLocale2"
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fournit la prise en charge de paramètres régionaux d'un fournisseur de port.  
  
## Syntaxe  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour définir les paramètres régionaux.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes **d'IDebugPortSupplierLocale2**.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Définit les paramètres régionaux du fournisseur de port.|  
  
## Configuration requise  
 en\-tête : Portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)