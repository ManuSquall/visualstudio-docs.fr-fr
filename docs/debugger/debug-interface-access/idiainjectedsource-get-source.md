---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "IDiaInjectedSource::get_source (méthode)"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les octets de code source.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Paramètres  
 `cbData`  
 \[in\]  Nombre d'octets qui représente la taille de la mémoire tampon de données.  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets qui représente les octets retournés.  Si `data` est `NULL`, alors `pcbData` correspond au nombre total d'octets de données disponibles.  
  
 `data[]`  
 \[out\]  Une mémoire tampon qui doit être effectuée avec les octets de source.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)