---
title: Serveurs (kit de développement logiciel Visual Studio) | Microsoft Docs
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
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199398"
---
# <a name="servers-visual-studio-sdk"></a>Serveurs (SDK Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, un **serveur**:  
  
- Est un conteneur de ports et de fournisseurs de ports, qui est utilisé pour communiquer des ports et des fournisseurs de ports aux moteurs de débogage de session (SDM) et de débogage.  
  
- Peut s’identifier par son nom et énumérer ses ports et fournisseurs de ports.  
  
- Est représenté par une interface [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , qui est implémentée uniquement par Visual Studio (une instance d’un serveur pour chaque instance de Visual Studio en cours d’exécution).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilis](../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
