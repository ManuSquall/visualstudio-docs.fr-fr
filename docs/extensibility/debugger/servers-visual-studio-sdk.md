---
title: "Serveurs (Kit de développement logiciel Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 404048e37f0a95ac1425250cfdcd098c4eb7f59d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (Kit de développement logiciel Visual Studio)
En termes de l’architecture du débogueur, une **server**:  
  
-   Est un conteneur de ports et les fournisseurs de port et est utilisé pour communiquer des ports et des fournisseurs de port pour le Gestionnaire de session de débogage (SDM) et les moteurs de débogage.  
  
-   Peut identifier par son nom et énumérer ses ports et les fournisseurs de port.  
  
-   Est représenté par un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, ce qui n’est implémentée par Visual Studio (une instance d’un serveur pour chaque instance de l’exécution de Visual Studio).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports](../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)