---
title: Serveurs (Visual Studio SDK) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712894"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
Dans l’architecture de débbugger, un *serveur*:

- Est un conteneur de ports et de fournisseurs portuaires et communique les ports et les fournisseurs portuaires au gestionnaire de débogé de session (SDM) et les moteurs de débogé.

- Peut s’identifier par son nom et énumérer ses ports et ses fournisseurs portuaires.

- Est représenté par une interface [IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) qui n’est implémentée que par Visual Studio (une instance d’un serveur pour chaque cas de Visual Studio en cours d’exécution).

## <a name="see-also"></a>Voir aussi
- [Ports](../../extensibility/debugger/ports.md)
- [Fournisseurs portuaires](../../extensibility/debugger/port-suppliers.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
