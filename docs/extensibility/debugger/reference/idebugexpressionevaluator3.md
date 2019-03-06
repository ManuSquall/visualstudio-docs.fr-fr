---
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb534d165cb3455eebe6417dc577b5b0657eb36
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720713"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un évaluateur d’expression (EE) avec une arborescence d’analyseur améliorée.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2
```

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette version de l’analyseur passe le fournisseur de symboles et l’adresse de l’image de l’évaluation.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interface, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Convertit une chaîne d’expression en une expression analysée, étant donnée le fournisseur de symboles et l’adresse de l’image de l’évaluation.|

## <a name="requirements"></a>Spécifications
 En-tête : EE.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll