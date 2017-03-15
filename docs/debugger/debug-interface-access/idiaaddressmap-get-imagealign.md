---
title: "IDiaAddressMap::get_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::get_imageAlign (méthode)"
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait l'alignement actuel d'image.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne la valeur d'inscription d'image du fichier exécutable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les images sont alignées aux limites de la mémoire spécifiques dépendant comment l'image a été chargée et créée.  L'inscription est généralement sur 1, 2, 4, 8, 16, 32, ou des limites de 64 octets.  L'inscription d'image peut être défini avec un appel à la méthode d' [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) .  
  
## Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)