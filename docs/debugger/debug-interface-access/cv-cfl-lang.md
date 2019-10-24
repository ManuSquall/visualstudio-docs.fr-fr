---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745333"
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

La langue de l' C++application CV_CFL_CXX est.

La langue de l’application CV_CFL_FORTRAN est FORTRAN.

La langue de l’application CV_CFL_MASM est Microsoft Macro Assembler.

La langue de l’application CV_CFL_PASCAL est Pascal.

La langue de l’application CV_CFL_BASIC est BASIC.

La langue de l’application CV_CFL_COBOL est COBOL.

L’application CV_CFL_LINK est un module généré par l’éditeur de liens.

L’application CV_CFL_CVTRES est un module de ressources converti à l’aide de l’outil CVTRES.

L’application CV_CFL_CVTPGD est un module PGO optimisé généré à l’aide de l’outil CVTPGD.

La langue de l' C#application CV_CFL_CSHARP est.

La langue de l’application CV_CFL_VB est Visual Basic.

Le langage d’application CV_CFL_ILASM est un assembly de langage intermédiaire (c’est-à-dire un assembly CLR (Common Language Runtime)).

La langue de l’application CV_CFL_JAVA est Java.

Le langage d’application CV_CFL_JSCRIPT est JScript.

Le langage d’application CV_CFL_MSIL est un langage MSIL (Microsoft Intermediate Language) inconnu, peut-être dû à l’utilisation du commutateur [/LTCG (génération de code durant l’édition de liens)](/cpp/build/reference/ltcg-link-time-code-generation) .

La langue de l’application CV_CFL_HLSL est le langage de nuanceur de haut niveau.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
