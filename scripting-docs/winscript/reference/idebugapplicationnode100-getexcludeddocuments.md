---
title: "IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::GetExcludedDocuments"
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::GetExcludedDocuments
Obtient les documents texte qui sont masqués par le filtre spécifié.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md) est implémenté par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetExcludedDocuments(  
        [in] APPLICATION_NODE_EVENT_FILTER filter,  
        [out] TEXT_DOCUMENT_ARRAY* pDocuments  
        );  
```  
  
#### Paramètres  
 `filter`  
 Filtre.  
  
 `pDocuments`  
 l'ensemble de documents.  
  
## Voir aussi  
 [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md)