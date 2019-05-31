---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35e012139b7df261f25ea524d0b13abf63b555e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349692"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un objet de tableau managé et permet à un évaluateur d’expression (EE) pour déterminer l’index de base (limites inférieures) pour le tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cela est implémenté par le moteur de débogage managé (DE).

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Récupère l’index de base (limites inférieures) pour chaque index étant donné le nombre de dimensions dans le tableau.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Détermine si le tableau a des index de base (limites inférieures) défini.|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour représenter des tableaux managés dans une arborescence d’analyse.

## <a name="requirements"></a>Configuration requise
 En-tête : EE.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll