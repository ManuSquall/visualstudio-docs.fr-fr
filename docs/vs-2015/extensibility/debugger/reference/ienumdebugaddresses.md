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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938470"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente une collection d’objets qui implémentent le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par le fournisseur de symboles pour fournir des jeux d’objets qui implémentent le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) (méthode).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère l’ensemble suivant de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objets à partir de l’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Réinitialise l’énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est généralement utilisée par le moteur de débogage pour aider à déterminer l’adresse appropriée afin de donner à l’évaluateur d’expression.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
