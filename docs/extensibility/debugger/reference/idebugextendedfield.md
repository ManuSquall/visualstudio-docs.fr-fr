---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a9e8f8e8414b6066bb8a407449a4b588d948bc4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333220"
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

## <a name="requirements"></a>Configuration requise
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll