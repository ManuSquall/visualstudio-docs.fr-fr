---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2373a26da1f6c3b327bea3a6f2402beb7d8bce45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196138"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente une collection d’objets qui implémentent l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par le fournisseur de symboles pour fournir des ensembles d’objets qui implémentent l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la méthode [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère le jeu d’objets [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) suivant de l’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Rétablit la première entrée de l’énumération.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est généralement utilisée par le moteur de débogage pour aider à déterminer l’adresse appropriée à attribuer à l’évaluateur d’expression.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces du fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
