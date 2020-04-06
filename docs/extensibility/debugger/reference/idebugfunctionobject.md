---
title: IDebugFunctionObject Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728491"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface représente une fonction.

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression implémente cette interface pour représenter une fonction.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est une spécialisation de l’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) et `IDebugObject` est obtenue à l’aide [de QueryInterface](/cpp/atl/queryinterface) sur l’interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l’interface `IDebugFunctionObject` expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crée un objet de données primitif.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crée un objet à l’aide d’un constructeur.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crée un objet sans constructeur.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crée un objet de tableau.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crée un objet à cordes.|
|[Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Appelle la fonction et renvoie la valeur résultante comme objet.|

## <a name="remarks"></a>Notes
 Cette interface permet à l’évaluateur d’expression de représenter les fonctions dans un arbre d’analyse. Les `Create` méthodes de cette interface sont utilisées pour construire des objets représentant les paramètres d’entrée de la méthode. La fonction peut alors être exécutée en appelant la méthode [d’évaluation,](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) qui renvoie un objet représentant la valeur de retour de la fonction.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
