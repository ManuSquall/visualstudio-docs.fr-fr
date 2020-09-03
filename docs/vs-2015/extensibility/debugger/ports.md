---
title: Ports | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153699"
---
# <a name="ports"></a>Ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, un **port**:  
  
- Est un conteneur pour un ensemble de processus s’exécutant sur un serveur. Par exemple, un port peut représenter une connexion à un appareil Windows CE par un câble série ou à un ordinateur non-DCOM en réseau. Un port spécial, appelé port local, contient tous les processus en cours d’exécution sur l’ordinateur local.  
  
- Peut s’identifier à l’aide d’un nom ou d’un identificateur.  
  
- Peut énumérer tous les processus en cours d’exécution sur le port et lancer et arrêter ces processus.  
  
- Est représenté par une interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , qui est créée en passant un argument [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) à [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit un port par défaut qui gère tous les processus Windows, natifs et gérés. Un port personnalisé doit être implémenté pour les connexions avec des périphériques externes qui ne sont pas basés sur Windows. Pour fournir de tels ports personnalisés, un fournisseur de port personnalisé doit également être implémenté.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
