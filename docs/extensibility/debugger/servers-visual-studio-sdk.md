---
title: Serveurs (kit de développement logiciel Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712894"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
Dans l’architecture du débogueur, un *serveur*:

- Est un conteneur de ports et fournisseurs de ports, et communique des ports et des fournisseurs de ports aux moteurs de débogage de session (SDM) et de débogage.

- Peut s’identifier par son nom et énumérer ses ports et fournisseurs de ports.

- Est représenté par une interface [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , qui est implémentée uniquement par Visual Studio (une instance d’un serveur pour chaque instance de Visual Studio en cours d’exécution).

## <a name="see-also"></a>Voir aussi
- [Ports](../../extensibility/debugger/ports.md)
- [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
