---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a22f8d60318721fbb51e0d5be7965c27666b8c48
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319761"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Étend la **IDebugTypeFieldBuilder** pour être en mesure de créer des types de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface peut être obtenue à partir du fournisseur de symboles.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) interface, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crée un tableau du type spécifié et de taille.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll