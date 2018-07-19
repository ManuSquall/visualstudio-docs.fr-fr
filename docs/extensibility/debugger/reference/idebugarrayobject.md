---
title: IDebugArrayObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cac7730296d2a4f95563c3d6ff4c60fdd294dc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106072"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour représenter un tableau.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pouvez obtenir cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface) si l’objet représente un tableau.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le `IDebugObject` interface, les méthodes suivantes sont implémentées sur le `IDebugArrayObject` interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtient le nombre d’éléments dans le tableau.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtient un élément du tableau.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtient tous les éléments du tableau.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtient le rang du tableau.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtient les dimensions du tableau.|  
  
## <a name="remarks"></a>Notes  
 Évaluateur d’expression utilise cette interface pour représenter des tableaux dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)