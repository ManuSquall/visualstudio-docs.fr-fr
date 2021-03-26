---
description: Représente une valeur d’énumération de type primitif à partir d’une interface IDebugField.
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 28abe0cb35074025263c684f9d9006fbfa7071c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071725"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Représente une valeur d’énumération de type primitif à partir d’une interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntaxe

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Récupère le type primitif associé à ce champ.|

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
