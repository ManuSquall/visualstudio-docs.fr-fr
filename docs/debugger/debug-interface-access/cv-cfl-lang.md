---
title: "CV_CFL_LANG | Microsoft Docs"
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
  - "CV_CFL_LANG (énumération)"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie le langage de code source de l'application ou du package lié.  
  
## Syntaxe  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Éléments  
 CV\_CFL\_C  
 le langage d'application est C.  
  
 CV\_CFL\_CXX  
 Le langage d'application est en C\+\+.  
  
 CV\_CFL\_FORTRAN  
 le langage d'application est FORTRAN.  
  
 CV\_CFL\_MASM  
 Le langage d'application est de Microsoft macro assembler.  
  
 CV\_CFL\_PASCAL  
 le langage d'application est Pascal.  
  
 CV\_CFL\_BASIC  
 Le langage d'application est PLACER LE.  
  
 CV\_CFL\_COBOL  
 le langage d'application est COBOL.  
  
 CV\_CFL\_LINK  
 l'application est un module éditeur de liens\-généré.  
  
 CV\_CFL\_CVTRES  
 L'application est un module de ressource converti à l'outil de CVTRES.  
  
 CV\_CFL\_CVTPGD  
 L'application est un module optimisé PGO généré à l'outil de CVTPGD.  
  
 CV\_CFL\_CSHARP  
 le langage d'application est C\#.  
  
 CV\_CFL\_VB  
 le langage d'application est Visual Basic.  
  
 CV\_CFL\_ILASM  
 Le langage d'application est assembly de langage intermédiaire \(autrement dit, assembly de runtime \(CLR\) CLS\).  
  
 CV\_CFL\_JAVA  
 Le langage d'application est Java.  
  
 CV\_CFL\_JSCRIPT  
 le langage d'application est Jscript.  
  
 CV\_CFL\_MSIL  
 Le langage d'application est inconnu Microsoft Intermediate langage \(MSIL\), probablement un résultat d'utiliser le commutateur de [\/LTCG \(Génération de code durant l'édition de liens\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) .  
  
 CV\_CFL\_HLSL  
 Le langage d'application est shader langage de haut niveau.  
  
## Notes  
 Les valeurs de cette énumération sont retournées par un appel à la méthode d' [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)