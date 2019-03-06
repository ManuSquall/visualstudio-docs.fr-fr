---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9126d7507f47852b7fc9bcd3777b112932892bb4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702146"
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

## <a name="requirements"></a>Spécifications
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll