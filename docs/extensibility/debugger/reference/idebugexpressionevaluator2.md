---
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7ae45b86db973e1358e5010b628a34bdd1d03e7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718155"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente une version améliorée d’un évaluateur d’expression (EE).

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par un évaluateur d’expression.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Récupère un objet de service selon son identificateur unique.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Précharge les modules désignés par le fournisseur du symbole spécifié.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Permet l’évaluateur d’expression (EE) spécifier l’interface de rappel que le moteur du débogueur (dé) utilisera pour lire les paramètres de mesure.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Définit le chemin d’accès pour le common language runtime (CLR) chargé dans le débogueur.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permet à un moteur de débogage passer un rappel à l’évaluateur d’expression lors de l’initialisation.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Arrête et nettoie l’évaluateur d’expression.|

## <a name="requirements"></a>Spécifications
 En-tête : EE.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll