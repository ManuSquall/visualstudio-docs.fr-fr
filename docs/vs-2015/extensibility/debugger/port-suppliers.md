---
title: Fournisseurs de port | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 173ff6b7550731262e8f4e3293b6f7c35eac4062
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858808"
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

