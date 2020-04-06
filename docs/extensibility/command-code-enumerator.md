---
title: Enumérateur de code de commande Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739788"
---
# <a name="command-code-enumerator"></a>Enumérateur de code de commande
Cet enumérateur est utilisé dans les options pour les [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et la [SccPopulateList](../extensibility/sccpopulatelist-function.md)pour indiquer la commande pour laquelle les options sont spécifiées.

## <a name="syntax"></a>Syntaxe

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Membres
SCC_COMMAND_GET correspond au [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT correspond à la [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN correspond à la [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT correspond à la [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD correspond à la [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE correspond au [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF correspond au [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY correspond à [l’histoire de la Scc](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME correspond à la [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES correspond aux [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS correspond à la [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
