---
title: Ports | Microsoft Docs
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
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f637c348295e709698d710016c80aa717613a068
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281760"
---
# <a name="ports"></a>Ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **port**:  
  
-   Un conteneur pour un ensemble de processus s’exécute sur un serveur. Par exemple, un port peut représenter une connexion à un périphérique Windows CE par un câble série ou à un ordinateur en réseau non-DCOM. Un seul port spécial, appelé le port local, contient tous les processus en cours d’exécution sur l’ordinateur local.  
  
-   Peut s’identifier par son nom ou identificateur.  
  
-   Peut énumérer tous les processus en cours d’exécution sur le port et lancer et mettre fin à ces processus.  
  
-   Est représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, ce qui est créé en passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) l’argument de [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit un port par défaut qui gère tous les processus basés sur Windows, natifs et managés. Un port personnalisé doit être implémenté pour les connexions avec des périphériques externes qui ne sont pas Windows. Pour fournir ces ports personnalisés, un fournisseur de port personnalisé doit également être implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

