---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abd220cd8c67318981fda79d3be8a0014ab61de1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321723"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un alias numérique pour une variable et permet un évaluateur d’expression (EE) pour obtenir le domaine d’application pour l’alias.

## <a name="syntax"></a>Syntaxe

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par le moteur de débogage managé (DE).

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Récupère l’identificateur pour le domaine d’application.|

## <a name="remarks"></a>Notes
 Un alias est un nombre décimal sous forme de chaîne suivie du caractère #, par exemple, 1001#.

## <a name="requirements"></a>Configuration requise
 En-tête : EE.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll