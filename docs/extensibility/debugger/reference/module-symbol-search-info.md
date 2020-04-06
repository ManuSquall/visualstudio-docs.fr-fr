---
title: MODULE_SYMBOL_SEARCH_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714243"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contient des informations d’état sur les chemins de recherche des symboles qui ont été recherchés.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Membres

`dwValidFields`\
Une combinaison de drapeaux de [l’SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération précisant le type d’information de recherche décrite dans cette structure.

`bstrVerboseSearchInfo`\
Chemin de recherche et résultats concatenated en une seule chaîne.

## <a name="remarks"></a>Notes

Cette structure est revenue d’un appel à la méthode [GetSymbolInfo.](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

Si `bstrVerboseSearchInfo` le champ n’est pas vide, alors il contient une liste des chemins recherchés et les résultats de cette recherche. La liste est formatée avec un chemin, suivi d’une ellipsis ("..."), suivie par le résultat. S’il y a plus d’une paire de résultats de chemin, alors chaque paire est séparée par une paire de « r’n » (carriage-return/linefeed). Le modèle ressemble à ceci:

\<chemin>... \<résultat>\<chemin>... \<résultat>\<chemin>... \<résultat>

Notez que la dernière entrée n’a pas de séquence de r’n.

Voici une `bstrVerboseSearchInfo` chaîne possible qui a été envoyé à la norme.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Spécifications

En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
