---
title: Fournisseurs de port | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950236"
---
# <a name="port-suppliers"></a>Fournisseurs de ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **fournisseur de port**:  
  
- Est contenue par un serveur et fournit des ports sur demande à ce serveur.  
  
- Peut ajouter et supprimer des ports à partir du serveur contenant.  
  
- Pouvez énumérer tous les ports dont il a fourni au serveur.  
  
- Est représenté par un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface, ce qui est inscrit avec Visual Studio via le Registre. Cette interface peut être obtenue en appelant [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit un fournisseur de port par défaut et un port par défaut. Si un port personnalisé doit être implémentée, un fournisseur de port personnalisé doit également être implémentées pour fournir ces ports personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
