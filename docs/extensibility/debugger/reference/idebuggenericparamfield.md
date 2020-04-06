---
title: IDebugGenericParamField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727839"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Représente un paramètre pour un type générique de code géré.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Utilisé pour le soutien des génériques.

## <a name="methods"></a>Méthodes
 En plus des méthodes de l’interface [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Retourne le nombre de contraintes associées à ce paramètre générique.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Récupère les contraintes associées à ce paramètre générique.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Récupère les drapeaux pour ce paramètre générique.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Récupère l’index de ce paramètre générique.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Récupère le nom de ce paramètre générique.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Récupère le type ou le propriétaire de la méthode de ce paramètre générique.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
