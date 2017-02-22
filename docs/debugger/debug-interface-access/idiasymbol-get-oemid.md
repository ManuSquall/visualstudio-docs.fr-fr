---
title: "IDiaSymbol::get_oemId | Microsoft Docs"
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
  - "IDiaSymbol::get_oemId (méthode)"
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_oemId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère la valeur du fabricant d'ordinateurs \(OEM\) OEM du symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur unique qui identifie OEM.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Cette propriété s'applique uniquement aux symboles avec un type de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) d' `SymTagCustomType`.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)