---
title: Serveurs (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111777"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
Dans l’architecture du débogueur, une *server*:

- Est un conteneur de ports et les fournisseurs de port et communique les ports et les fournisseurs de port pour le Gestionnaire de session de débogage (SDM) et les moteurs de débogage.

- Peut s’identifier par son nom et énumérer ses ports et les fournisseurs de port.

- Est représenté par un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, qui est implémentée uniquement par Visual Studio (une seule instance d’un serveur pour chaque instance en cours d’exécution de Visual Studio).

## <a name="see-also"></a>Voir aussi
- [Ports](../../extensibility/debugger/ports.md)
- [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)