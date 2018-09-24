---
title: Modules | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8750c1f6676966be8564fbf4a175a66fa180a401
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233163"
---
# <a name="modules"></a>Modules
En termes d’architecture du débogueur, une *module*:  
  
-   Est un conteneur physique de code, comme un fichier exécutable ou une DLL.  
  
-   Peut recharger ses symboles et décrire lui-même. Descriptions de module sont affichées dans la fenêtre Modules de l’IDE.  
  
-   Est représenté par un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, créée par un moteur de débogage pour décrire le module.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)