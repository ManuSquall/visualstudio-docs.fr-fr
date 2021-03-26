---
description: Étend le IDebugTypeFieldBuilder pour pouvoir créer des types de tableau.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48bdc4f1bb2668b83da3b042df194e73045e45fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083516"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Étend le **IDebugTypeFieldBuilder** pour pouvoir créer des types de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface peut être obtenue à partir du fournisseur de symboles.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) , cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crée un tableau du type et de la taille spécifiés.|

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
