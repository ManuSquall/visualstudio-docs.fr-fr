---
title: CV_CFL_LANG | Microsoft Docs
description: Obtenir des informations sur le type d’énumération CV_CFL_LANG, qui spécifie le langage de code de l’application ou du module lié dans le kit de développement logiciel (SDK) debug interface Access.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46c20fbe0c46a6c964a05b92ccd3a8bcf73cd1f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857369"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Spécifie la langue du code source de l’application ou du module lié.

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
La langue de l’application CV_CFL_C est C.

CV_CFL_CXX langage de l’application est C++.

La langue de l’application CV_CFL_FORTRAN est FORTRAN.

CV_CFL_MASM langage de l’application est Microsoft Macro Assembler.

La langue de l’application CV_CFL_PASCAL est Pascal.

CV_CFL_BASIC langage de l’application est de base.

CV_CFL_COBOL langage de l’application est COBOL.

CV_CFL_LINK application est un module généré par l’éditeur de liens.

CV_CFL_CVTRES application est un module de ressources converti à l’aide de l’outil CVTRES.

CV_CFL_CVTPGD application est un module PGO optimisé généré avec l’outil CVTPGD.

CV_CFL_CSHARP langage de l’application est C#.

La langue de l’application CV_CFL_VB est Visual Basic.

CV_CFL_ILASM langage de l’application est un assembly de langage intermédiaire (c’est-à-dire un assembly CLR (Common Language Runtime)).

La langue de l’application CV_CFL_JAVA est Java.

CV_CFL_JSCRIPT langage de l’application est JScript.

CV_CFL_MSIL langage de l’application est un langage MSIL (Microsoft Intermediate Language) inconnu, éventuellement dû à l’utilisation du commutateur [/LTCG (génération de code durant l’édition de liens)](/cpp/build/reference/ltcg-link-time-code-generation) .

CV_CFL_HLSL langage de l’application est le langage de nuanceur de haut niveau.

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
