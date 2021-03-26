---
description: Représente la capacité de créer un champ qui représente un type.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bf2199766cd0e78940c38e8441fe9fb0ab3c320
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083490"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Représente la capacité de créer un champ qui représente un type.

## <a name="syntax"></a>Syntaxe

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est obtenue à partir du fournisseur de symboles.

## <a name="methods"></a>Méthodes
 Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crée un objet qui représente un type primitif.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crée un pointeur vers le type spécifié.|

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
