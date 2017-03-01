---
title: IDebugPointerObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 11
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
ms.openlocfilehash: ad0660d583e1bc23c19b0fbd1836eb952d778665
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet pointeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 L’évaluateur d’expression implémente cette interface pour représenter un objet pointeur.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface peut obtenir cette interface à l’aide de [QueryInterface](/visual-cpp/atl/queryinterface) si la `IDebugObject` représente un pointeur.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), le `IDebugPointerObject` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Suppression de la référence](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtient l’objet vers lequel pointe l’interface.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtient la valeur à laquelle l’interface désigne comme une série d’octets consécutifs.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Définit la valeur à laquelle l’interface pointe à partir d’une série d’octets consécutifs.|  
  
## <a name="remarks"></a>Notes  
 Un évaluateur d’expression utilise cette interface pour représenter un pointeur dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
