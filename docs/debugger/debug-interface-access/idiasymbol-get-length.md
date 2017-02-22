---
title: "IDiaSymbol::get_length | Microsoft Docs"
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
  - "IDiaSymbol::get_length (méthode)"
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le nombre de bits ou d'octets de mémoire utilisés par l'objet représenté par ce symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne le nombre d'octets ou de bits de la mémoire utilisés par l'objet représenté par ce symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 si [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) du symbole est `LocIsBitField`, la longueur retournée par cette méthode est dans des bits ; sinon, la longueur est en octets pour tous les autres types d'emplacement.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v7.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)