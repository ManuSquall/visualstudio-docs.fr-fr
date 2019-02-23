---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed0b7300fca935a88b6da9e878d87f5ce443bec9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682815"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Étend les types de champs qui sont disponibles pour prendre en charge les génériques du code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Récupère le type de champ étendues spécifié.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Détermine si le champ représente un type fermé.|

## <a name="requirements"></a>Spécifications
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll