---
title: "Ports | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports"
  - "débogage (débogage SDK), des ports"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ports
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quant à l'architecture du débogueur, **un port**:  
  
-   Est un conteneur pour un ensemble de processus qui s'exécutent sur un serveur.  Par exemple, un port peut représenter une connexion à un appareil Windows CE par un câble série, ou un ordinateur du réseau de non\-DCOM.  Un port spécial, appelé le port local, contient tous les processus en cours de exécution sur l'ordinateur local.  
  
-   Peut s'identifient de nom ou l'identificateur.  
  
-   Peut énumérer tous les processus exécuter sur le port et démarrer et arrêter ces processus.  
  
-   Est représenté par une interface d' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , qui est créée lorsque vous passez un argument d' [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) à [Ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un port par défaut qui effectue tous les processus Windows, natif et managé.  Un port personnalisé doit être implémenté pour les connexions à les systèmes externes qui ne sont pas Windows.  Pour fournir de ces ports personnalisés, les besoins personnalisés d'un fournisseur de port également à implémenter.  
  
## Voir aussi  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)