---
title: "IDiaEnumFrameData::Skip | Microsoft Docs"
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
  - "IDiaEnumFrameData::Skip (méthode)"
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignore un nombre spécifié d'éléments de données de frame dans une séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Paramètres  
 celt  
 \[in\]  Le nombre d'éléments de données de frame de la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s'il ne reste plus d'enregistrements à ignorer.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)