---
title: Fournisseurs de port | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e134b9b4adeb45693a9841a0a867a9c3630bf2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835102"
---
# <a name="port-suppliers"></a>Fournisseurs de port
Dans l’architecture du débogueur, une *fournisseur de port*:  
  
- Est contenue par un serveur et fournit des ports sur demande à ce serveur.  
  
- Peut ajouter et supprimer des ports à partir du serveur contenant.  
  
- Pouvez énumérer tous les ports dont il a fourni au serveur.  
  
- Est représenté par un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface, ce qui est inscrit avec Visual Studio via le Registre. Cette interface peut être obtenue en appelant [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un fournisseur de port par défaut et un port par défaut. Si un port personnalisé doit être implémentée, un fournisseur de port personnalisé doit également être implémentées pour fournir ces ports personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)