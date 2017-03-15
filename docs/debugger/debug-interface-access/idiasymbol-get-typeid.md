---
title: "IDiaSymbol::get_typeId | Microsoft Docs"
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
  - "IDiaSymbol::get_typeId (méthode)"
ms.assetid: b40be36e-10e1-463c-9c6d-21862679d29f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_typeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait l'identificateur de type du symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_typeId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'ID du type du symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 l'identificateur est une valeur unique créée par le diamètre Kit de développement logiciel pour marquer tous les symboles comme unique.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)