---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09c0ce6f8b641830b76fffd0d201b430ddf00b41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962246"
---
# <a name="idebugaddress"></a>IDebugAddress
Cette interface représente l’adresse d’un élément. Elle est retournée par le Gestionnaire de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface pour représenter une adresse d’un objet.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 De nombreuses méthodes sur le nombre d’interfaces retournent cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Récupère un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure qui décrit un objet et son emplacement.|  
  
## <a name="remarks"></a>Notes  
 Le fournisseur de symboles retourne cette interface pour représenter un objet et son emplacement au sein d’une étendue particulière (par exemple, fonction, méthode ou classe). Cette interface est retournée à partir d’et passée à différentes méthodes de fournisseur de symboles et de l’expression évaluateur. Normalement, le fournisseur de symboles est la seule entité qui a besoin d’interpréter le contenu de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)