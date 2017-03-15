---
title: "IDiaPropertyStorage::ReadBSTR | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBSTR"
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit les valeurs d' `BSTR` dans un jeu de propriétés.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur de la propriété à lire \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `pValue`  
 \[out\]  Retourne la valeur de propriété.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `E_INVALIDARG` si la propriété n'est pas de type `BSTR`.  
  
## Notes  
 `BSTR` est défini par windows comme une chaîne à caractères larges se terminant par zéro.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)