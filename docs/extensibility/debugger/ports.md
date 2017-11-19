---
title: Ports | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 926f5e9a80a91da57d843c11175865f78775e38c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ports"></a>Ports
En termes de l’architecture du débogueur, une **port**:  
  
-   Un conteneur pour un ensemble de processus s’exécute sur un serveur. Par exemple, un port peut représenter une connexion à un périphérique Windows CE par un câble série ou à un ordinateur en réseau non-DCOM. Un port spécial, appelé le port local, contient tous les processus en cours d’exécution sur l’ordinateur local.  
  
-   Peut identifier par son nom ou identificateur.  
  
-   Peut énumérer tous les processus en cours d’exécution sur le port et lancer et mettre fin à ces processus.  
  
-   Est représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, qui est créé en passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argument [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit un port par défaut qui gère tous les processus basé sur Windows, natifs et managés. Un port personnalisé doit être implémenté pour les connexions avec des périphériques externes qui ne sont pas basés sur Windows. Pour fournir ces ports personnalisés, un fournisseur de port personnalisé doit également être implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)