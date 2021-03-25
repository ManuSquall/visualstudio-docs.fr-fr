---
description: Active un moteur de débogage qui utilise DCOM pour demander à l’interface utilisateur de Visual Studio de s’assurer que le pare-feu ne bloque pas le débogage distant.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c67cc1ab9335cfeb197ca67937510b3137d6432c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073610"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Active un moteur de débogage qui utilise DCOM pour demander [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à l’interface utilisateur de s’assurer que le pare-feu ne bloque pas le débogage distant.

## <a name="syntax"></a>Syntaxe

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Implémenté par l’objet Port du gestionnaire de débogage de session.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugFirewallConfigurationCallback2` .

|Méthode|Description|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Demande que le pare-feu ne bloque pas le débogage distant.|

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
