---
title: CV_CFL_LANG | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 12dfcf493432116fcba36d55d1a85b977e9058b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Spécifie le langage de code source de l’application ou d’un module lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
 Langue de l’application est C.  
  
 CV_CFL_CXX  
 Langue de l’application est en C++.  
  
 CV_CFL_FORTRAN  
 Langue de l’application est FORTRAN.  
  
 CV_CFL_MASM  
 Langue de l’application est Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Langue de l’application est Pascal.  
  
 CV_CFL_BASIC  
 Langue de l’application est BASIC.  
  
 CV_CFL_COBOL  
 Langue de l’application est COBOL.  
  
 CV_CFL_LINK  
 Application est un module généré par l’éditeur de liens.  
  
 CV_CFL_CVTRES  
 Application est un module de ressource converti avec l’outil CVTRES.  
  
 CV_CFL_CVTPGD  
 Application est un module de PGO optimisé généré avec l’outil CVTPGD.  
  
 CV_CFL_CSHARP  
 Langue de l’application est c#.  
  
 CV_CFL_VB  
 Langue de l’application est Visual Basic.  
  
 CV_CFL_ILASM  
 Langue de l’application est un assembly de langage intermédiaire (autrement dit, les assembly de Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Langue de l’application est Java.  
  
 CV_CFL_JSCRIPT  
 Langue de l’application est Jscript.  
  
 CV_CFL_MSIL  
 Langue de l’application est un inconnu langage MSIL (Microsoft Intermediate), éventuellement un résultat de l’utilisation de la [/LTCG (génération de Code d’édition de liens)](/cpp/build/reference/ltcg-link-time-code-generation) basculer.  
  
 CV_CFL_HLSL  
 Langue de l’application est un langage HLSL.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par un appel à la [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)