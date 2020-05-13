---
title: IDebugModOpt - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726978"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Représente un modificateur optionnel de débogé.

## <a name="syntax"></a>Syntaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Notes pour les appelants
 Obtenu à partir d’un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente une classe ou une méthode.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Récupère une liste de modificateurs optionnels.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
