---
title: "Serveurs (Kit de développement logiciel Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2db4c9968cb585cab40c8b0138e610812483952d
ms.lasthandoff: 02/22/2017

---
# <a name="servers-visual-studio-sdk"></a>Serveurs (Kit de développement logiciel Visual Studio)
En termes de l’architecture du débogueur, une **server**:  
  
-   Est un conteneur de ports et les fournisseurs de port et est utilisé pour communiquer des ports et des fournisseurs de port pour le Gestionnaire de session de débogage (SDM) et moteurs de débogage.  
  
-   Peut identifier par son nom et énumérer ses ports et les fournisseurs de port.  
  
-   Est représenté par une [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, ce qui n’est implémentée par Visual Studio (une instance d’un serveur pour chaque instance en cours d’exécution de Visual Studio).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports](../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
