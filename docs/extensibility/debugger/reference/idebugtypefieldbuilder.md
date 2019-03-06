---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 456fe2656949e0cc862acdb97149b85f037beac8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720104"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Représente la capacité de créer un champ qui représente un type.

## <a name="syntax"></a>Syntaxe

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est obtenue à partir du fournisseur de symboles.

## <a name="methods"></a>Méthodes
 Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crée un objet qui représente un type primitif.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crée un pointeur vers le type spécifié.|

## <a name="requirements"></a>Spécifications
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll