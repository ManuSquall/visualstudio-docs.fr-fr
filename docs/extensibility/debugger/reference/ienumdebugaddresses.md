---
title: IEnumDebugAddresses | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses
helpviewer_keywords: IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db531c35ea3bbb6176095f19897404d192096e22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Cette interface représente une collection d’objets implémentant le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par le fournisseur de symbole pour fournir des ensembles d’objets qui implémentent la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) (méthode).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère l’ensemble suivant de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objets à partir de l’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Réinitialise l’énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface est généralement utilisée par le moteur de débogage pour aider à déterminer l’adresse adéquate afin de donner à l’évaluateur d’expression.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)