---
title: Ijsdebugframe, Interface | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame, interface
Représente un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Évaluer une expression dans le contexte de ce frame de pile.|  
|[Méthode IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Retourne un Explorateur de propriétés pour ce frame de pile.|  
|[Méthode IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.|  
|[Méthode IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.|  
|[Méthode IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Obtient le nom convivial du frame de pile.|  
|[Méthode IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Obtient l’adresse de retour envoyée à la 'start' (voir GetStackRange) de l’image.|  
|[Méthode IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Retourne la plage d’adresses absolues du frame de pile JavaScript logique.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)