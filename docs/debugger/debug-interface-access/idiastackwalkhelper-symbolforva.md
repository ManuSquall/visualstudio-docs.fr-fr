---
title: "IDiaStackWalkHelper::symbolForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::symbolForVA (méthode)"
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le symbole qui contient l'adresse virtuelle spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### Paramètres  
 `va`  
 \[in\]  Adresse virtuelle contenue dans le symbole demandé.  le symbole doit être `SymTagFunctionType` \(une valeur de l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).  
  
 `ppSymbol`  
 \[out\]  un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole à l'adresse spécifiée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)