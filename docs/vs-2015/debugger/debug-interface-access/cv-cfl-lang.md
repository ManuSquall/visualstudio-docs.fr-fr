---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699361"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie la langue du code source de l’application ou du module lié.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements"></a>Éléments  
 CV_CFL_C  
 La langue de l’application est C.  
  
 CV_CFL_CXX  
 Le langage de l’application est C++.  
  
 CV_CFL_FORTRAN  
 La langue de l’application est FORTRAN.  
  
 CV_CFL_MASM  
 La langue de l’application est Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 La langue de l’application est Pascal.  
  
 CV_CFL_BASIC  
 La langue de l’application est de base.  
  
 CV_CFL_COBOL  
 La langue de l’application est COBOL.  
  
 CV_CFL_LINK  
 L’application est un module généré par l’éditeur de liens.  
  
 CV_CFL_CVTRES  
 L’application est un module de ressources converti à l’aide de l’outil CVTRES.  
  
 CV_CFL_CVTPGD  
 L’application est un module PGO optimisé généré avec l’outil CVTPGD.  
  
 CV_CFL_CSHARP  
 Le langage de l’application est C#.  
  
 CV_CFL_VB  
 La langue de l’application est Visual Basic.  
  
 CV_CFL_ILASM  
 Le langage de l’application est un assembly de langage intermédiaire (c’est-à-dire un assembly CLR (Common Language Runtime)).  
  
 CV_CFL_JAVA  
 La langue de l’application est Java.  
  
 CV_CFL_JSCRIPT  
 Le langage de l’application est JScript.  
  
 CV_CFL_MSIL  
 Le langage de l’application est un langage MSIL (Microsoft Intermediate Language) inconnu, éventuellement dû à l’utilisation du commutateur [/LTCG (génération de code durant l’édition de liens)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 La langue de l’application est le langage de nuanceur de haut niveau.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
