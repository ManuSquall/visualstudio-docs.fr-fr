---
title: IDebugArrayField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
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
ms.openlocfilehash: e73ab513461077ed44bec2eed7410f5317fb6a4e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayfield"></a>IDebugArrayField
Cette interface décrit un symbole de tableau ou un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Cette interface est une spécialisation qui représente les objets du tableau.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/visual-cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne l’indicateur `FIELD_TYPE_ARRAY`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, cette interface implémente les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Obtient le nombre d’éléments contenus dans le tableau.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Obtient le type d’élément dans le tableau.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Obtient le rang du tableau.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
