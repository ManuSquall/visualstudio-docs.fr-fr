---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911869a1d727e466cbf2d43557946efaba1f7dd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922828"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Étend la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interface pour permettre l’extraction des interfaces de module et de processus.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Implémenté par les moteurs de débogage et consommé par le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] déboguer le package.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur le `IDebugCodeContext2` interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Récupère une référence à l’interface du module de débogage.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Récupère une référence à l’interface du processus de débogage.|

## <a name="remarks"></a>Notes
 Il s’agit d’une interface facultative qui n’a généralement pas être implémentée.

## <a name="requirements"></a>Configuration requise
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll