---
title: "IDiaEnumFrameData::frameByRVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByRVA (méthode)"
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne un frame par l'adresse virtuelle associée \(RVA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Paramètres  
 relativeVirtualAddress  
 \[in\]  RVA du frame d'intérêt.  
  
 frame  
 \[out\]  Retourne un objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) représentant le frame qui contient l'adresse fournie.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si données de frame ne correspond pas à l'adresse spécifiée.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)