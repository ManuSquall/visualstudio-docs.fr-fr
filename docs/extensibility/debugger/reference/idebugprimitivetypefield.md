---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4012b919cffc5e16433567fac283ac731d4d215c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353276"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Représente une valeur d’énumération de type primitif à partir d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.

## <a name="syntax"></a>Syntaxe

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Récupère le type primitif associé à ce champ.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll