---
title: "IDiaEnumFrameData::frameByVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByVA (méthode)"
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne un frame par l'adresse virtuelle \(VA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Paramètres  
 virtualAddress  
 \[in\]  VA du frame d'intérêt.  
  
 frame  
 \[out\]  Retourne un objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame qui contient l'adresse fournie.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si données de frame ne correspond pas à l'adresse spécifiée.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)