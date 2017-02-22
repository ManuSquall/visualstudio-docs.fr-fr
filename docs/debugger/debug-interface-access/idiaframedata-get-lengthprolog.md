---
title: "IDiaFrameData::get_lengthProlog | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthProlog (méthode)"
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_lengthProlog
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre d'octets du code de prologue dans le bloc.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre d'octets du code de prologue.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Le code du prologue est une séquence d'instructions qui conserve des registres, définit l'état de l'UC, et génère la pile pour la fonction.  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)