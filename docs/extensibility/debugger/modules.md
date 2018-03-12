---
title: Modules | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8371bb2fd985062f6e44d97ae720878ad54b06d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modules"></a>Modules
En termes de l’architecture du débogueur, une **module**:  
  
-   Est un conteneur physique de code, par exemple un fichier exécutable ou une DLL.  
  
-   Permet de recharger les symboles et de se décrire lui-même. Descriptions de module sont affichées dans la fenêtre Modules de l’IDE.  
  
-   Est représenté par un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, créée par un moteur de débogage pour décrire le module.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)