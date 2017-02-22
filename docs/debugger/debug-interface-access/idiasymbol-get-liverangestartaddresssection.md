---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne la partie de la section de l'adresse de début de la plage dans laquelle le symbole local est valide.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### Paramètres  
 `section`  
 \[out\]  Retourne la partie de la section de la plage d'adresses de départ.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
> [!NOTE]
>  Code d'erreur retourné signifie que le symbole n'a pas les informations dynamiques de la plage.  
  
## Notes  
 L'adresse formée par la section et l'offset est le début de la plage dans laquelle le symbole est valide.  
  
 Pour obtenir la partie de l'adresse offset, utilisez [IDiaSymbol::get\_liveRangeStartAddressOffset](../Topic/IDiaSymbol::get_liveRangeStartAddressOffset.md).  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)