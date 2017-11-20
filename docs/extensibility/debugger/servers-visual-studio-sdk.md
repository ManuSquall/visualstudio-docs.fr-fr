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
ms.openlocfilehash: 496e9b361dbb7f5c3eb5cf5197a1351a1182af3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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