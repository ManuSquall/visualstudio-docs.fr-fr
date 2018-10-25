---
title: Ports | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f54ec931bc34f854d1c9f1a85961f5af65a56264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936340"
---
# <a name="ports"></a>Ports
Dans l’architecture du débogueur, une *port*:  
  
- Un conteneur pour un ensemble de processus s’exécute sur un serveur. Par exemple, un port peut représenter une connexion à un périphérique Windows CE par un câble série ou à un ordinateur en réseau non-DCOM. Un seul port spécial, appelé le port local, contient tous les processus en cours d’exécution sur l’ordinateur local.  
  
- Peut s’identifier par son nom ou identificateur.  
  
- Peut énumérer tous les processus en cours d’exécution sur le port et lancer et mettre fin à ces processus.  
  
- Est représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, ce qui est créé en passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) l’argument de [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un port par défaut qui gère tous les processus basés sur Windows, natifs et managés. Un port personnalisé doit être configuré pour les connexions avec des périphériques externes qui ne sont pas Windows. Pour fournir ces ports personnalisés, vous devez également configurer un fournisseur de port personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)