---
title: Ports (en anglais) Microsoft Docs
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
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738310"
---
# <a name="ports"></a>Ports
Dans l’architecture débbugger, un *port*:

- Est un conteneur pour un ensemble de processus en cours d’exécution sur un serveur. Par exemple, un port peut représenter une connexion à un appareil Windows CE par un câble en série ou à une machine en réseau non-DCOM. Un port spécial, appelé le port local, contient tous les processus fonctionnant sur la machine locale.

- Peut s’identifier par nom ou identifiant.

- Peut énumérer tous les processus en cours d’exécution sur le port et lancer et mettre fin à ces processus.

- Est représenté par une interface [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) qui est créé en passant un argument [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) à [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit un port par défaut qui gère tous les processus basés sur Windows, à la fois natifs et gérés. Un port personnalisé doit être configuré pour les connexions avec des périphériques externes qui ne sont pas basés sur Windows. Pour fournir ces ports personnalisés, vous devez également mettre en place un fournisseur de port personnalisé.

## <a name="see-also"></a>Voir aussi
- [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processus](../../extensibility/debugger/processes.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
