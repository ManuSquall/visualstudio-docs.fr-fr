---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2a60572c652080f2655ab7fe33954a661fbe07e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319737"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Permet d’interroger pour plus d’informations sur l’ordinateur cible.

## <a name="syntax"></a>Syntaxe

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par les objets de port du Gestionnaire de session de débogage.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugWindowsComputerPort2`.

|Méthode|Description|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Récupère des informations sur l’ordinateur sur lequel le débogueur dans en cours d’exécution.|

## <a name="requirements"></a>Configuration requise
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll