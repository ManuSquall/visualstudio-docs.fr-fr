---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit les valeurs d' `LONG` dans un jeu de propriétés.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur de la propriété à lire \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `pValue`  
 \[out\]  Retourne la valeur de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `E_INVALIDARG` si la propriété n'est pas de type `LONG`.  
  
## Notes  
 `LONG` est défini par windows en tant qu'entier signé 32 bits.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)