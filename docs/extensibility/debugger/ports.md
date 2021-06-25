---
title: Ports | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un port dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900770"
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
