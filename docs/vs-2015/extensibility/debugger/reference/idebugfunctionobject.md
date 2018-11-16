---
title: IDebugFunctionObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56a0e0c7dffa23698e83214e8a1b4293e68be210
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804018"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Cette interface est une spécialisation de la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface et est obtenue en utilisant [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur la `IDebugObject` interface.  
  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

