---
title: "IDiaEnumFrameData::Item | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData::Item (méthode)"
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait un élément de données de frame au moyen d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) à récupérer.  L'index est comprise entre 0 et `count`\-1, où `count` est retourné par la méthode d' [IDiaEnumFrameData::get\_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .  
  
 section  
 \[out\]  Retourne un objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) représentant l'élément de données souhaité de frame.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)