---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
Détermine si le document spécifié appartient à l'un des nœuds enfants de ce nœud.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md) est implémenté par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### Paramètres  
 `pSearchKey`  
 La clé de recherche.  
  
## Voir aussi  
 [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md)