---
title: IDebugFirewallConfigurationCallback2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728711"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Permet à un moteur de débogage [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] qui utilise DCOM de demander à l’interface utilisateur pour s’assurer que le pare-feu ne bloquera pas le débogage à distance.

## <a name="syntax"></a>Syntaxe

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Mis en œuvre par l’objet bâbord du gestionnaire de débogé de session.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugFirewallConfigurationCallback2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Demande que le pare-feu ne bloque pas le débogage à distance.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
