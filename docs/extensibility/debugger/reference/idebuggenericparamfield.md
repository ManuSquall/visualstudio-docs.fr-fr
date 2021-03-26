---
description: Représente un paramètre pour un type générique de code managé.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091927"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Représente un paramètre pour un type générique de code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Utilisé pour la prise en charge des génériques.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Retourne le nombre de contraintes associées à ce paramètre générique.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Récupère les contraintes associées à ce paramètre générique.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Récupère les indicateurs pour ce paramètre générique.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Récupère l’index de ce paramètre générique.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Récupère le nom de ce paramètre générique.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Récupère le type ou le propriétaire de méthode de ce paramètre générique.|

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
