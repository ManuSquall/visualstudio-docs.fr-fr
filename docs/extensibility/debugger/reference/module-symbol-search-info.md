---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714243"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contient des informations d’État sur les chemins de recherche de symboles qui ont été recherchés.

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
Combinaison d’indicateurs de l’énumération [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) qui spécifie le type d’informations de recherche décrit dans cette structure.

`bstrVerboseSearchInfo`\
Le chemin de recherche et les résultats sont concaténés dans une chaîne unique.

## <a name="remarks"></a>Notes

Cette structure est retournée à partir d’un appel à la méthode [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .

Si le `bstrVerboseSearchInfo` champ n’est pas vide, il contient une liste de chemins d’accès recherchés et les résultats de cette recherche. La liste est mise en forme avec un chemin d’accès, suivi par des points de suspension (« ... »), suivi du résultat. S’il existe plus d’une paire de résultats de chemin, chaque paire est séparée par une paire « \r\n » (retour chariot/saut de seconde). Le modèle ressemble à ceci :

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Notez que la dernière entrée n’a pas de séquence \r\n.

Voici une chaîne possible `bstrVerboseSearchInfo` qui a été envoyée à la sortie standard.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Spécifications

En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
