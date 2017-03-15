---
title: "IDiaSymbol::get_udtKind | Microsoft Docs"
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
  - "IDiaSymbol::get_udtKind (méthode)"
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait le dossier fichiers divers un type défini par l' \(UDT\)utilisateur.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération d' [UdtKind, énumération](../../debugger/debug-interface-access/udtkind.md) qui spécifie le type de type défini par l'utilisateur : structure, classe, ou union.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [UdtKind, énumération](../../debugger/debug-interface-access/udtkind.md)