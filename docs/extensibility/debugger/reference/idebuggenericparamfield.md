---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab5cb19475ae92ab1e89bdce5c833e0f18a2cccb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720704"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Représente un paramètre pour un type générique du code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Utilisé pour la prise en charge des génériques.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Retourne le nombre de contraintes qui sont associés à ce paramètre générique.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Récupère les contraintes qui sont associés à ce paramètre générique.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Récupère les indicateurs pour ce paramètre générique.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Récupère l’index de ce paramètre générique.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Récupère le nom de ce paramètre générique.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Récupère le type ou la méthode le propriétaire de ce paramètre générique.|

## <a name="requirements"></a>Spécifications
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll