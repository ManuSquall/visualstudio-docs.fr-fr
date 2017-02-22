---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit les valeurs d' `DWORD` dans un jeu de propriétés.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur de la propriété à lire \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `pValue`  
 \[out\]  Retourne la valeur de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `E_INVALIDARG` si la propriété n'est pas de type `DWORD`.  
  
## Notes  
 `DWORD` est défini par windows comme un entier non signé 32 bits.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)