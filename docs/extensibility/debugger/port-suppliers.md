---
title: Fournisseurs de ports (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738298"
---
# <a name="port-suppliers"></a>Fournisseurs portuaires
Dans l’architecture de débbugger, un *fournisseur de port*:

- Est contenu par un serveur et fournit des ports sur demande à ce serveur.

- Peut ajouter et supprimer les ports du serveur contenant.

- Peut énumérer tous les ports qu’il a fournis au serveur.

- Est représenté par une interface [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) qui est enregistrée auprès de Visual Studio par le biais du registre. Cette interface peut être obtenue en appelant [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit un fournisseur de port par défaut et un port par défaut. Si un port personnalisé doit être mis en œuvre, un fournisseur de port personnalisé doit également être mis en œuvre pour fournir ces ports personnalisés.

## <a name="see-also"></a>Voir aussi
- [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
