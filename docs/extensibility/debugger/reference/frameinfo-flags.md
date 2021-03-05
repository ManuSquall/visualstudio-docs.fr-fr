---
description: Spécifie les informations à récupérer sur un objet de frame de pile.
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4029212aae6d4557e17c42a0c0e024a83c94b0a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150820"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Spécifie les informations à récupérer sur un objet de frame de pile.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FRAMEINFO_FLAGS {
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
public enum enum_FRAMEINFO_FLAGS {
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
Initialiser/utiliser le `m_bstrFuncName` champ.

`FIF_RETURNTYPE`\
Initialiser/utiliser le `m_bstrReturnType` champ.

`FIF_ARGS`\
Initialiser/utiliser le `m_bstrArgs` champ.

`FIF_LANGUAGE`\
Initialiser/utiliser le `m_bstrLanguage` champ.

`FIF_MODULE`\
Initialiser/utiliser le `m_bstrModule` champ.

`FIF_STACKRANGE`\
Initialisez/utilisez les `m_addrMin` `m_addrMax` champs et (plage de pile).

`FIF_FRAME`\
Initialiser/utiliser le `m_pFrame` champ.

`FIF_DEBUGINFO`\
Initialiser/utiliser le `m_fHasDebugInfo` champ.

`FIF_STALECODE`\
Initialiser/utiliser le `m_fStaleCode` champ.

`FIF_ANNOTATEDFRAME`\
Initialiser/utiliser le `m_fAnnotatedFrame` champ.

`FIF_DEBUG_MODULEP`\
Initialiser/utiliser le `m_pModule` champ.

`FIF_FUNCNAME_FORMAT`\
Met en forme le nom de la fonction. Le résultat est retourné dans le `m_bstrFunName` champ et aucun autre champ n’est rempli.

`FIF_FUNCNAME_RETURNTYPE`\
Ajoute le type de retour au `m_bstrFuncName` champ.

`FIF_FUNCNAME_ARGS`\
Ajoute les arguments au `m_bstrFuncName` champ.

`FIF_FUNCNAME_LANGUAGE`\
Ajoute la langue au `m_bstrFuncName` champ.

`FIF_FUNCNAME_MODULE`\
Ajoute le nom du module au `m_bstrFuncName` champ.

`FIF_FUNCNAME_LINES`\
Ajoute le nombre de lignes au `m_bstrFuncName` champ.

`FIF_FUNCNAME_OFFSET`\
Ajoute au `m_bstrFuncName` champ le décalage en octets à partir du début de la ligne si `FIF_FUNCNAME_LINES` est spécifié. Si `FIF_FUNCNAME_LINES` n’est pas spécifié, ou si les numéros de ligne ne sont pas disponibles, ajoute le décalage en octets à partir du début de la fonction.

`FIF_FUNCNAME_ARGS_TYPES`\
Ajoute le type de chaque argument de fonction au `m_bstrFuncName` champ.

`FIF_FUNCNAME_ARGS_NAMES`\
Ajoute le nom de chaque argument de fonction au `m_bstrFuncName` champ.

`FIF_FUNCNAME_ARGS_VALUES`\
Ajoute la valeur de chaque argument de fonction au `m_bstrFuncName` champ.

`FIF_FUNCNAME_ARGS_ALL`\
Ajoute le type, le nom et la valeur de tous les arguments au `m_bstrFuncName` champ.

`FIF_ARGS_TYPES`\
Les types d’arguments sont récupérés et mis en forme.

`FIF_ARGS_NAMES`\
Les noms d’arguments sont récupérés et mis en forme.

`FIF_ARGS_VALUES`\
Les valeurs d’argument sont extraites et mises en forme.

`FIF_ARGS_ALL`\
Récupérez et mettez en forme le type, le nom et la valeur de tous les arguments.

`FIF_ARGS_NOFORMAT`\
Spécifie que les arguments ne sont pas mis en forme (par exemple, n’ajoutez pas de parenthèses ouvrantes et fermantes autour de la liste d’arguments ni d’ajouter un séparateur entre les arguments).

`FIF_ARGS_NO_FUNC_EVAL`\
Spécifie que l’évaluation de la fonction (propriété) ne doit pas être utilisée lors de la récupération des valeurs d’arguments.

`FIF_FILTER_NON_USER_CODE`\
Le moteur de débogage consiste à filtrer les frames de code non-utilisateur afin qu’ils ne soient pas inclus.

`FIF_ARGS_NO_TOSTRING`\
N’autorisez pas l' `ToString()` évaluation ou la mise en forme des fonctions lors du retour des arguments de fonction.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Les informations de frame doivent être extraites du domaine App-Domain hébergé et non du processus d’hébergement.

## <a name="remarks"></a>Notes
Ces indicateurs sont passés aux méthodes [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) et [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) pour indiquer les champs à initialiser dans la structure ou les structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .

Ces indicateurs sont également utilisés pour indiquer les champs de la structure [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) qui sont utilisés et valides lorsque la structure est retournée. Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
