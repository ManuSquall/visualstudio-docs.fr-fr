---
title: Serveurs (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516750"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [serveurs (SDK Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
En termes d’architecture du débogueur, une **server**:  
  
-   Est un conteneur de ports et les fournisseurs de port et est utilisé pour communiquer les ports et les fournisseurs de port pour le Gestionnaire de session de débogage (SDM) et de déboguer les moteurs.  
  
-   Peut s’identifier par son nom et énumérer ses ports et les fournisseurs de port.  
  
-   Est représenté par un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, qui est implémentée uniquement par Visual Studio (une seule instance d’un serveur pour chaque instance en cours d’exécution de Visual Studio).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports](../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

