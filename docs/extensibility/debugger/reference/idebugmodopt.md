---
description: Représente un modificateur facultatif Debug.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 047c01f78931e1b13110640952c67c11a68bc8a2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149858"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Représente un modificateur facultatif Debug.

## <a name="syntax"></a>Syntaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Notes pour les appelants
 Obtenu à partir d’un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente une classe ou une méthode.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Récupère une liste de modificateurs facultatifs.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
