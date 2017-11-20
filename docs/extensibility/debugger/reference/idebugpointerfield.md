---
title: IDebugPointerField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerField
helpviewer_keywords: IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 554be41beaca8696f299b7f71d889b8a2fbbfc2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Cette interface représente un type pointeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le fournisseur de symbole implémente cette interface pour représenter un pointeur.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes sur le `IDebugField` et `IDebugContainerField` interfaces, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant la cible du pointeur.|  
  
## <a name="remarks"></a>Remarques  
 En C/C++, un pointeur peut être un conteneur s’il est utilisé avec la notation de tableau. Par exemple, prenons `char *pString`, `pString` a un type de pointeur vers `char`. `pString[3]`a le type d’un conteneur qui est un pointeur vers `char` qui référence le quatrième élément du conteneur.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)