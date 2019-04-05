---
title: Serveurs (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81de310320fe45c06f2a233d7c8d742f9d55405e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938092"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **server**:  
  
-   Est un conteneur de ports et les fournisseurs de port et est utilisé pour communiquer les ports et les fournisseurs de port pour le Gestionnaire de session de débogage (SDM) et de déboguer les moteurs.  
  
-   Peut s’identifier par son nom et énumérer ses ports et les fournisseurs de port.  
  
-   Est représenté par un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, qui est implémentée uniquement par Visual Studio (une seule instance d’un serveur pour chaque instance en cours d’exécution de Visual Studio).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports](../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
