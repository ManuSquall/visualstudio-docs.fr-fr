---
title: "IDiaSymbol::get_relativeVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_relativeVirtualAddress (méthode)"
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère l'adresse virtuelle relative \(RVA\) de l'emplacement.  Utilisez lorsque [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) est défini à `LocIsStatic`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne l'adresse virtuelle relative de l'emplacement.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pSymbol;  
DWORD       rva;  
pSymbol->get_relativeVirtualAddress( &rva );  
```  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)