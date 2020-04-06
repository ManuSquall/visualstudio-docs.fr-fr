---
title: IDebugWindowsComputerPort2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718225"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Permet de demander des informations sur l’ordinateur cible.

## <a name="syntax"></a>Syntaxe

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les objets portuaires du gestionnaire de débogé de session.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugWindowsComputerPort2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetComputerInfo (en anglais)](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Récupère des informations sur l’ordinateur sur lequel le débbuggeur en cours d’exécution.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
