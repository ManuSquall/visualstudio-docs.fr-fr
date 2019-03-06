---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b681b8e6b3ece72144f6b9dd5c18bc7c0b4145
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682898"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Permet à un moteur de débogage qui utilise DCOM pour demander le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour vous assurer que le pare-feu ne bloquera pas le débogage à distance.

## <a name="syntax"></a>Syntaxe

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Implémenté par l’objet de port du Gestionnaire de session de débogage.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugFirewallConfigurationCallback2`.

|Méthode|Description|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Demande que le pare-feu bloque le débogage distant.|

## <a name="requirements"></a>Spécifications
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll