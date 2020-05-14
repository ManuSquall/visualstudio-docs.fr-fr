---
title: FRAMEINFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736800"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Spécifie les informations à récupérer sur un objet de cadre de pile.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Champs
`FIF_FUNCNAME`\
Initialiser/utiliser `m_bstrFuncName` le champ.

`FIF_RETURNTYPE`\
Initialiser/utiliser `m_bstrReturnType` le champ.

`FIF_ARGS`\
Initialiser/utiliser `m_bstrArgs` le champ.

`FIF_LANGUAGE`\
Initialiser/utiliser `m_bstrLanguage` le champ.

`FIF_MODULE`\
Initialiser/utiliser `m_bstrModule` le champ.

`FIF_STACKRANGE`\
Initialiser/utiliser `m_addrMin` les `m_addrMax` champs et (gamme de piles).

`FIF_FRAME`\
Initialiser/utiliser `m_pFrame` le champ.

`FIF_DEBUGINFO`\
Initialiser/utiliser `m_fHasDebugInfo` le champ.

`FIF_STALECODE`\
Initialiser/utiliser `m_fStaleCode` le champ.

`FIF_ANNOTATEDFRAME`\
Initialiser/utiliser `m_fAnnotatedFrame` le champ.

`FIF_DEBUG_MODULEP`\
Initialiser/utiliser `m_pModule` le champ.

`FIF_FUNCNAME_FORMAT`\
Formats le nom de la fonction. Le résultat est `m_bstrFunName` retourné sur le terrain et aucun autre champ n’est rempli.

`FIF_FUNCNAME_RETURNTYPE`\
Ajoute le type `m_bstrFuncName` de retour sur le terrain.

`FIF_FUNCNAME_ARGS`\
Ajoute les arguments `m_bstrFuncName` sur le terrain.

`FIF_FUNCNAME_LANGUAGE`\
Ajoute la langue `m_bstrFuncName` au terrain.

`FIF_FUNCNAME_MODULE`\
Ajoute le nom `m_bstrFuncName` du module sur le terrain.

`FIF_FUNCNAME_LINES`\
Ajoute le nombre de `m_bstrFuncName` lignes sur le terrain.

`FIF_FUNCNAME_OFFSET`\
Ajoute au `m_bstrFuncName` champ le décalage dans les octets `FIF_FUNCNAME_LINES` dès le début de la ligne si elle est spécifiée. Si `FIF_FUNCNAME_LINES` elle n’est pas spécifiée, ou si les numéros de ligne ne sont pas disponibles, ajoute le décalage dans les octets dès le début de la fonction.

`FIF_FUNCNAME_ARGS_TYPES`\
Ajoute le type de chaque `m_bstrFuncName` argument de fonction au champ.

`FIF_FUNCNAME_ARGS_NAMES`\
Ajoute le nom de chaque `m_bstrFuncName` argument de fonction au champ.

`FIF_FUNCNAME_ARGS_VALUES`\
Ajoute la valeur de chaque `m_bstrFuncName` argument de fonction au champ.

`FIF_FUNCNAME_ARGS_ALL`\
Ajoute le type, le nom et `m_bstrFuncName` la valeur de tous les arguments sur le terrain.

`FIF_ARGS_TYPES`\
Les types d’arguments sont récupérés et formatés.

`FIF_ARGS_NAMES`\
Les noms d’argument sont récupérés et formatés.

`FIF_ARGS_VALUES`\
Les valeurs d’argument sont récupérées et formatées.

`FIF_ARGS_ALL`\
Récupérez et formatez le type, le nom et la valeur de tous les arguments.

`FIF_ARGS_NOFORMAT`\
Précise que les arguments ne sont pas formatés (par exemple, n’ajoutez pas d’ouverture et de clôture entre parenthèses autour de la liste d’arguments ni ajoutez un séparateur entre les arguments).

`FIF_ARGS_NO_FUNC_EVAL`\
Précise que l’évaluation de la fonction (propriété) ne doit pas être utilisée lors de la récupération des valeurs de l’argument.

`FIF_FILTER_NON_USER_CODE`\
Le moteur de débogé est de filtrer les cadres de code non-utilisateur afin qu’ils ne soient pas inclus.

`FIF_ARGS_NO_TOSTRING`\
N’autorisez pas l’évaluation `ToString()` ou le formatage des fonctions lors du retour des arguments de la fonction.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Les informations de cadre doivent être obtenues à partir de l’application hébergée-domaine plutôt que le processus d’hébergement.

## <a name="remarks"></a>Notes
Ces drapeaux sont transmis aux méthodes [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) et [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) pour indiquer quels champs doivent être parasélisés dans la structure ou les structures [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

Ces drapeaux sont également utilisés pour indiquer quels champs de la structure [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) sont utilisés et valides lorsque la structure est retournée. Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
