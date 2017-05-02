---
title: "IJsDebugFrame, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugFrame, interface
Représente un frame de pile.  
  
## Syntaxe  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## Membres  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[IJsDebugFrame::Evaluate, méthode](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Évaluez une expression dans le contexte de ce frame de pile.|  
|[IJsDebugFrame::GetDebugProperty, méthode](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Retourne un explorateur de propriétés pour ce frame de pile.|  
|[IJsDebugFrame::GetDocumentPositionWithId, méthode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Retourne la position actuelle de ce frame de pile dans le document de niveau utilisateur.|  
|[IJsDebugFrame::GetDocumentPositionWithName, méthode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Retourne la position actuelle de ce frame de pile dans le document de niveau utilisateur.|  
|[IJsDebugFrame::GetName, méthode](../../winscript/reference/ijsdebugframe-getname-method.md)|Obtient le nom convivial du frame de pile.|  
|[IJsDebugFrame::GetReturnAddress, méthode](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Obtient l'adresse de retour envoyée au « début » \(consultez GetStackRange\) du frame.|  
|[IJsDebugFrame::GetStackRange, méthode](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Retourne la plage d'adresses absolue du frame de pile JavaScript logique.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)