---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory (méthode)"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit un bloc de données de l'image du fichier exécutable en mémoire.  
  
## Syntaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Paramètres  
 `type`  
 \[in\]  Une valeur de l'énumération de [MemoryTypeEnum, énumération](../../debugger/debug-interface-access/memorytypeenum.md) spécifiant le type de mémoire à lire.  
  
 va  
 \[in\]  Adresse virtuelle dans l'image de laquelle commencer à lire.  
  
 `cbData`  
 \[in\]  la taille de la mémoire tampon de données en octets.  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets le effectue.  Si `pbData` est `NULL`, alors c'est le seul le nombre d'octets de données disponibles.  
  
 `pbData`  
 \[in, out\]  Une mémoire tampon qui est terminée avec l'indiquer de mémoire.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum, énumération](../../debugger/debug-interface-access/memorytypeenum.md)