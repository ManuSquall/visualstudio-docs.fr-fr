---
title: IDebugBinder3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735671"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface donne accès à des types, des alias et des services de visualisation personnalisé.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogé implémente cette interface pour prendre en charge les alias, les services de visualisation personnalisé et l’accès à des informations de type objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Une interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obtient cette interface en utilisant [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 En plus des méthodes fournies par l’interface [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) cette interface implémente ce qui suit :

|Méthode|Description|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Récupère un objet mémoire représentant la mémoire à laquelle cet objet est lié.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Récupère l’exception associée à cet objet (le cas échéant),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Récupère un pseudonyme donné son nom,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Récupère une gamme de tous les alias pour cet objet,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtient le nombre de types d’arguments associés à cet objet,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Récupère une liste de types d’arguments associés à cet objet,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtient une interface à un service de visualisation,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convertit soit un emplacement d’objet, soit une adresse mémoire 64 bits dans un contexte de mémoire.|

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
