---
title: "IDiaSymbol::get_container | Microsoft Docs"
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
  - "IDiaSymbol::get_container (méthode)"
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette fonction extrait un pointeur vers un symbole représentant le parent\/conteneur de ce symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne un pointeur vers `IDiaSymbol` contenant des informations concernant le conteneur de ce symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne S\_FALSE ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour de S\_FALSE signifie que la propriété n'est pas disponible pour le symbole.  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v8.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)