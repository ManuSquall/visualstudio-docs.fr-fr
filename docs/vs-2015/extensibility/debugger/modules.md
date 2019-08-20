---
title: Modules | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153751"
---
# <a name="modules"></a>Modules
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **module**:  
  
- Est un conteneur physique de code, comme un fichier exécutable ou une DLL.  
  
- Peut recharger ses symboles et décrire lui-même. Descriptions de module sont affichées dans la fenêtre Modules de l’IDE.  
  
- Est représenté par un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, créée par un moteur de débogage pour décrire le module.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
