---
description: Représente la somme de contrôle d’un document pour une demande de point d’arrêt.
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bb0bdd70d2d4d1d56e341bc8f21ef1127433219
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173707"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Représente la somme de contrôle d’un document pour une demande de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] package de débogage et consommé par les moteurs de débogage.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugBreakpointChecksumRequest2` .

|Méthode|Description|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Récupère la somme de contrôle du document pour une demande de point d’arrêt en fonction de l’identificateur unique de l’algorithme de somme de contrôle à utiliser.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Détermine si la somme de contrôle est activée pour ce document.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
