---
title: "IDiaSymbol::get_platform | Microsoft Docs"
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
  - "IDiaSymbol::get_platform (méthode)"
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type de plateforme pour laquelle le module \(compiland\) a été compilé.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération de [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) qui spécifie le type de plateforme pour laquelle le module \(compiland\) a été compilé.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)