---
title: "IDiaSymbol::get_age | Microsoft Docs"
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
  - "IDiaSymbol::get_age (méthode)"
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_age
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la valeur d'âge d'un fichier .pdb.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne la valeur d'âge d'un fichier .pdb.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 L'âge ne correspond toujours à aucune valeur d'heure ; il est généralement utilisée pour déterminer si un fichier .pdb est pas synchronisé avec un fichier .exe correspondant.  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v7.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)