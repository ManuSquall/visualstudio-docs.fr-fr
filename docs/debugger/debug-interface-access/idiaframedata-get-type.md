---
title: "IDiaFrameData::get_type | Microsoft Docs"
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
  - "IDiaFrameData::get_type (méthode)"
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type du frame de compilateur\-détail.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération de [StackFrameTypeEnum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md) qui indique le type de frame de compilateur\-détail.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md)