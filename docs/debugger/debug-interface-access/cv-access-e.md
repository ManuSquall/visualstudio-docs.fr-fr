---
title: "CV_access_e | Microsoft Docs"
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
  - "CV_access_e (énumération)"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

spécifie la portée de la visibilité \(niveau d'accès\) des fonctions membres et des variables.  
  
## Syntaxe  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Éléments  
 CV\_private  
 Le membre a un accès privé.  
  
 CV\_protected  
 Le membre protégé l'accès.  
  
 CV\_public  
 le membre a accès public.  
  
## Notes  
 Le spécificateur d'accès d' `friend` n'est pas inclus ici car elle est généralement utilisé par les fonctions non \- membres qui ont accès aux éléments privés et protégés de la classe.  Utilisez la méthode d' [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) pour rechercher des symboles avec accès d' `SymTagFriend` .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)