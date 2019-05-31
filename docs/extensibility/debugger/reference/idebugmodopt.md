---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9f8fa5e496056eac2a30114f4062f635775350b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324047"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Représente un modificateur facultatif de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Obtenu à partir d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet qui représente une classe ou une méthode.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Récupère une liste des modificateurs facultatifs.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll