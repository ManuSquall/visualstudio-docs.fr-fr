---
title: Ports | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un port dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13ca62f841525ef91ac7d66b67c09da54cabeb3
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606556"
---
# <a name="ports"></a>Ports
Dans l’architecture du débogueur, un *port*:

- Est un conteneur pour un ensemble de processus s’exécutant sur un serveur. Par exemple, un port peut représenter une connexion à un appareil Windows CE par un câble série ou à un ordinateur non-DCOM en réseau. Un port spécial, appelé port local, contient tous les processus en cours d’exécution sur l’ordinateur local.

- Peut s’identifier à l’aide d’un nom ou d’un identificateur.

- Peut énumérer tous les processus en cours d’exécution sur le port et lancer et arrêter ces processus.

- Est représenté par une interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , qui est créée en passant un argument [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) à [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un port par défaut qui gère tous les processus Windows, natifs et gérés. Un port personnalisé doit être configuré pour les connexions avec des périphériques externes qui ne sont pas basés sur Windows. Pour fournir de tels ports personnalisés, vous devez également configurer un fournisseur de ports personnalisé.

## <a name="see-also"></a>Voir aussi
- [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processus](../../extensibility/debugger/processes.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
