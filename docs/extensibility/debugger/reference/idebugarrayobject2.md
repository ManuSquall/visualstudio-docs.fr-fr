---
title: IDebugArrayObject2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736223"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Représente un objet de tableau géré, et permet à un évaluateur d’expression (EE) de déterminer l’indice de base (limites inférieures) pour le tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Ceci est mis en œuvre par le moteur de débogé géré (DE).

## <a name="methods"></a>Méthodes
 En plus des méthodes de l’interface [IDebugArrayObject,](../../../extensibility/debugger/reference/idebugarrayobject.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Récupère les indices de base (limites inférieures) pour chaque indice compte tenu du nombre de dimensions dans le tableau.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Détermine si le tableau a défini des indices de base (limites inférieures).|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour représenter les tableaux gérés dans un arbre d’analyse.

## <a name="requirements"></a>Spécifications
 En-tête: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
