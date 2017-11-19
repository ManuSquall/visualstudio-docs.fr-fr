---
title: IDebugAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress
helpviewer_keywords: IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f009002e9c454b1e10cac13c297e067da9c44ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddress"></a>IDebugAddress
Cette interface représente l’adresse d’un élément. Elle est retournée par le Gestionnaire de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface pour représenter une adresse d’un objet.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 De nombreuses méthodes de nombreuses interfaces retournent cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Récupère un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure qui décrit un objet et son emplacement.|  
  
## <a name="remarks"></a>Remarques  
 Le fournisseur de symbole retourne cette interface pour représenter un objet et son emplacement dans une étendue particulière (par exemple, fonction, méthode ou classe). Cette interface est retournée à partir d’et passée à différentes méthodes de fournisseur de symboles et de l’expression évaluateur. En règle générale, le fournisseur de symboles est la seule entité qui doit interpréter le contenu de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)