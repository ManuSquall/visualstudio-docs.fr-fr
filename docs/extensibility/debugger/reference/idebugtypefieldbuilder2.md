---
title: IDebugTypeFieldBuilder2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718301"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Étend **l’IDebugTypeFieldBuilder** pour être en mesure de créer des types de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface peut être obtenue auprès du fournisseur de symboles.

## <a name="methods"></a>Méthodes
 En plus des méthodes de l’interface [IDebugTypeFieldBuilder,](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crée un tableau du type et de la taille spécifiés.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
