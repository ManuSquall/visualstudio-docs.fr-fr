---
title: IDebugExpressionEvaluator2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729145"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Représente une version améliorée d’un évaluateur d’expression (EE).

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un évaluateur d’expression.

## <a name="methods"></a>Méthodes
 En plus des méthodes de l’interface [IDebugExpressionEvaluator,](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[Getservice](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Récupère un objet de service compte tenu de son identifiant unique.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Précharge les modules désignés par le fournisseur de symboles spécifié.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Permet à l’évaluateur d’expression (EE) de spécifier l’interface de rappel que le moteur de débogénaire (DE) utilisera pour lire les paramètres métriques.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Définit le chemin vers le temps de course de langue commune (CLR) chargé dans le débbugger.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permet à un moteur de débogé de passer un rappel à l’évaluateur d’expression lors de l’initialisation.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Arrête et nettoie l’évaluateur d’expression.|

## <a name="requirements"></a>Spécifications
 En-tête: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
