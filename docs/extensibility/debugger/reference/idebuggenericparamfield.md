---
description: Représente un paramètre pour un type générique de code managé.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4ab1cd79826e2f9f07a4f325d701be4e9eb9c9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172569"
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

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
