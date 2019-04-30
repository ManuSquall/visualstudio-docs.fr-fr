---
title: Énumérateur de Code de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddb2e88db15d60731bc17fcc60cb69772779f14e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927008"
---
# <a name="command-code-enumerator"></a>Énumérateur de code de commande
Cet énumérateur est utilisé dans les options pour le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md)pour indiquer la commande pour laquelle les options sont spécifiées.

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
SCC_COMMAND_GET correspond à la [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT correspond à la [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN correspond à la [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT correspond à la [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD correspond à la [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE correspond à la [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF correspond à la [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY correspond à la [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME correspond à la [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES correspond à la [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS correspond à la [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
