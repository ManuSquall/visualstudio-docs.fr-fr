---
title: IDebugAddress2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 005911465f7ba78a3a6dcdf8249a96443cd12355
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaddress2"></a>IDebugAddress2
Cette interface fournit l’accès à l’ID du processus qui possède l’objet dont l’adresse est représentée par cette interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Cette interface fournit l’accès à l’ID du processus qui possède l’objet qui est associée à cette adresse.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/visual-cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre de vtable  
 Outre les méthodes héritées de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Récupère l’ID de processus qui possède l’objet représenté par cette interface.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
