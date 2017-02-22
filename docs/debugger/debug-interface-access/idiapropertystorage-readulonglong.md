---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit les valeurs d' `ULONGLONG` dans un jeu de propriétés.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur de la propriété à lire \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `pValue`  
 \[out\]  Retourne la valeur de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `E_INVALIDARG` si la propriété n'est pas de type `ULONGLONG`.  
  
## Notes  
 `ULONGLONG` est défini par windows en tant qu'entier non signé 64 bits.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)