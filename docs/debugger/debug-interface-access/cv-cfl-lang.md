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
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555041"
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
Langue de l’Application de CV_CFL_C est C.

Langue de l’Application de CV_CFL_CXX est C++.

Langue de l’Application de CV_CFL_FORTRAN est FORTRAN.

Langue de l’Application de CV_CFL_MASM est Microsoft Macro Assembler.

Langue de l’Application de CV_CFL_PASCAL est Pascal.

Langue de l’Application de CV_CFL_BASIC est BASIC.

Langue de l’Application de CV_CFL_COBOL est COBOL.

Application de CV_CFL_LINK est un module généré par l’éditeur de liens.

Application de CV_CFL_CVTRES est un module de ressources converti avec l’outil CVTRES.

Application de CV_CFL_CVTPGD est un module de PGO optimisé généré avec CVTPGD outil.

Langue de l’Application de CV_CFL_CSHARP est C#.

Langue de l’Application de CV_CFL_VB est Visual Basic.

Langue de l’Application de CV_CFL_ILASM est un assembly de langage intermédiaire (autrement dit, les assembly de Common Language Runtime (CLR)).

Langue de l’Application de CV_CFL_JAVA est Java.

Langue de l’Application de CV_CFL_JSCRIPT est Jscript.

Langue de l’Application de CV_CFL_MSIL est un inconnu langage MSIL (Microsoft Intermediate), éventuellement un résultat de l’utilisation de la [/LTCG (Link-time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) basculer.

Langue de l’Application de CV_CFL_HLSL est High Level Shader Language.

## <a name="remarks"></a>Notes
Les valeurs dans cette énumération sont retournées par un appel à la [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
