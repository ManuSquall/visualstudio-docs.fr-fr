---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit les valeurs d' `BOOL` dans un jeu de propriétés.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur de la propriété à lire \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `pValue`  
 \[out\]  Retourne la valeur de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `E_INVALIDARG` si la propriété n'est pas de type `BOOL`.  
  
## Notes  
 Pour des résultats cohérents, interprétez la valeur d' `BOOL` afin que les valeurs différentes de zéro soient `TRUE` et zéro est `FALSE`.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)