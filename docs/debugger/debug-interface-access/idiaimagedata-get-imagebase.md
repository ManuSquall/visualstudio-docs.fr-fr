---
title: "IDiaImageData::get_imageBase | Microsoft Docs"
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
  - "IDiaImageData::get_imageBase (méthode)"
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait l'emplacement mémoire où l'image doit être basée.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne la valeur suggérée de base d'image.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En raison de conflits de base d'image, une image peut être réinstallé automatiquement à un emplacement mémoire non utilisée lorsqu'il est chargé.  Cette méthode retourne l'indicateur de base \(emplacement de mémoire proposé\) que ait été stocké dans le module au moment de la compilation.  
  
## Voir aussi  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)