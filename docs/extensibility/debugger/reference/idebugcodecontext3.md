---
title: IDebugCodeContext3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734189"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Étend l’interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) pour permettre la récupération des interfaces de module et de processus.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par les moteurs [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de débogé et consommé par le paquet Debug.

## <a name="methods"></a>Méthodes
 En plus des méthodes `IDebugCodeContext2` de l’interface, cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetModule (en)](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Récupère une référence à l’interface du module de débogé.|
|[GetProcess (en)](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Récupère une référence à l’interface du processus de débogé.|

## <a name="remarks"></a>Notes
 Il s’agit d’une interface facultative qui n’a généralement pas besoin d’être implémentée.

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
