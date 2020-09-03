---
title: Fournisseurs de port | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738298"
---
# <a name="port-suppliers"></a>Fournisseurs de port
Dans l’architecture du débogueur, un *fournisseur de port*:

- Est contenu par un serveur et fournit des ports à la demande de ce serveur.

- Permet d’ajouter et de supprimer des ports du serveur contenant.

- Peut énumérer tous les ports qu’il a fournis au serveur.

- Est représenté par une interface [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , qui est inscrite auprès de Visual Studio via le registre. Cette interface peut être obtenue en appelant [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un fournisseur de ports par défaut et un port par défaut. Si un port personnalisé doit être implémenté, un fournisseur de port personnalisé doit également être implémenté pour fournir ces ports personnalisés.

## <a name="see-also"></a>Voir aussi
- [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
