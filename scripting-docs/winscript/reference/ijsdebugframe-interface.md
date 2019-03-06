---
title: Interface IJsDebugFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa491a02d289a0a92a70348ec5ef483dd8f8467
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093299"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame, interface
Représente un frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|[Méthode IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Obtient l’adresse de retour envoyée au « début » (consultez GetStackRange) du cadre.|  
|[Méthode IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Retourne la plage d’adresse absolue du frame de pile JavaScript logique.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)