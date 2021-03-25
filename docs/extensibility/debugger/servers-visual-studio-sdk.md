---
title: Serveurs (kit de développement logiciel Visual Studio) | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un serveur dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7bb19262d4ce5fd1b3139f05cd9bbc57131db1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070360"
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
