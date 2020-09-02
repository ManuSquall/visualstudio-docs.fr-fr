---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728431"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente une fonction et améliore l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression (EE) implémente cette interface pour représenter une fonction.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Les méthodes de cette interface diffèrent celles de **IDebugFunctionObject** des manières suivantes :

- La méthode **IDebugEvaluate** prend des indicateurs.

- La méthode **CreateObject** prend des indicateurs et un délai d’attente.

- La méthode **CreateStringObjectWithLength** prend une longueur.

## <a name="methods"></a>Méthodes
 Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crée un objet qui utilise un constructeur donné des paramètres d’indicateur d’évaluation et une valeur de délai d’attente.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crée un objet String qui a la longueur spécifiée.|
|[Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Appelle la fonction et retourne la valeur résultante sous la forme d’un objet.|

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
