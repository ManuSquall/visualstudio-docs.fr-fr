---
title: IDebugManagedObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e096d7c11e044f62f82fb8162aac5553e38b3a29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface permet à l’évaluateur d’expression (EE) pour appeler des méthodes ou propriétés sur les instances de classe de valeur (par exemple, `System.Decimal`) et pour définir leur valeur sans appeler [évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sur le programme en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Évaluateur d’expression implémente cette interface pour représenter un objet de code managé comme une variable.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Pour obtenir cette interface, appelez [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) sur une [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente une instance d’une classe value.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), le `IDebugManagedObject` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retourne une interface qui représente l’objet de code managé et à partir de tout le code managé approprié interface peut être obtenue.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Définit la valeur de cet objet à la valeur d’un objet de code managé spécifié.|  
  
## <a name="remarks"></a>Notes  
 Évaluateur d’expression utilise cette interface pour stocker un objet de code managé dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)