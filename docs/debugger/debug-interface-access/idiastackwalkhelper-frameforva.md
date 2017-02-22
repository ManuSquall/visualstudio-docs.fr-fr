---
title: "IDiaStackWalkHelper::frameForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::frameForVA (méthode)"
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::frameForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le frame de pile qui contient l'adresse virtuelle spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT frameForVA(   
   ULONGLONG        va,  
   IDiaFrameData**  ppFrame  
);  
```  
  
#### Paramètres  
 `va`  
 \[in\]  Adresse virtuelle pour les données de frame.  
  
 `ppFrame`  
 \[out\]  un objet d' [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame de pile à l'adresse spécifiée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)