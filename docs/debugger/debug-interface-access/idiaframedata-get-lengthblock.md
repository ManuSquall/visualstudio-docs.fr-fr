---
title: "IDiaFrameData::get_lengthBlock | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthBlock (méthode)"
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_lengthBlock
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait la longueur, en octets, du bloc de code décrit par le frame.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre d'octets du code dans le frame.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 La valeur retournée par cette méthode est généralement utilisée dans l'interprétation d'une chaîne de programme \(consultez la méthode d' [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) pour la définition d'une chaîne de programme\).  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)