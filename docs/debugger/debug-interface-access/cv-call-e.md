---
title: "CV_call_e | Microsoft Docs"
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
  - "CV_call_e (énumération)"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie la convention d'appel d'une fonction.  
  
> [!NOTE]
>  Seules les valeurs d'énumération les plus courantes sont documentées ici.  L'énumération complète est disponible dans le fichier d'en\-tête de cvconst.h.  
  
## Syntaxe  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Éléments  
 CV\_CALL\_NEAR\_C  
 Spécifie une convention d'appel de fonction à l'aide d'une transmission de type push de droite à gauche proche.  l'appel de la fonction désactive la pile.  
  
 CV\_CALL\_NEAR\_FAST  
 Spécifie une convention d'appel de fonction à l'aide d'une transmission de type push de gauche à droite collaboration avec des registres.  La fonction appelée utilise la somme d'octets de paramètre pour désactiver la pile.  
  
 CV\_CALL\_NEAR\_STD  
 Spécifie une convention d'appel de fonction à l'aide d'un appel standard fermant \(modèle push de droite à gauche\).  
  
 CV\_CALL\_NEAR\_SYS  
 Spécifie une convention d'appel de fonction à l'aide d'un appel système proche.  
  
 CV\_CALL\_THISCALL  
 Spécifie une convention d'appel de fonction à l'aide de l'appel d' `this` \(pointeur d'`this` passé dans le registre\).  
  
 CV\_CALL\_CLRCALL  
 Spécifie une convention d'appel de fonction utilisée par le common langage \(CLR\) runtime \(également appelé une convention d'appel de code managé\).  
  
## Notes  
 Les valeurs de cette énumération sont retournées par un appel à la méthode d' [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)