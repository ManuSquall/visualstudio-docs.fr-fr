---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61da63d0d9a46cb47cd2bc14a7e2bcf1945ca4de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043308"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un évaluateur d’expression implémente cette interface pour représenter une fonction.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est une spécialisation de la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface et est obtenue en utilisant [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugObject` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), le `IDebugFunctionObject` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crée un objet de données primitif.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crée un objet à l’aide d’un constructeur.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crée un objet avec aucun constructeur.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crée un objet tableau.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crée un objet de chaîne.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Appelle la fonction et retourne la valeur obtenue en tant qu’objet.|  
  
## <a name="remarks"></a>Notes  
 Cette interface permet à l’évaluateur d’expression représenter des fonctions dans une arborescence d’analyse. Le `Create` méthodes dans cette interface sont utilisées pour construire des objets représentant les paramètres d’entrée à la méthode. La fonction peut ensuite être exécutée en appelant le [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) (méthode), qui retourne un objet représentant la valeur de retour de la fonction.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)