---
title: 'IDebugModule3 :: GetSymbolInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726893"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Récupère une liste de chemins d’accès dans lesquels des symboles sont recherchés, ainsi que les résultats de la recherche de chaque chemin d’accès.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
dans Combinaison d’indicateurs de l’énumération [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) spécifiant les champs `pInfo` à remplir.

`pInfo`\
à Structure [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) dont les membres doivent être renseignés avec les informations spécifiées. S’il s’agit d’une valeur null, cette méthode retourne `E_INVALIDARG` .

## <a name="return-value"></a>Valeur renvoyée
Si la méthode est réussie, elle retourne `S_OK` ; sinon, elle retourne un code d’erreur.

> [!NOTE]
> La chaîne retournée (dans la `MODULE_SYMBOL_SEARCH_INFO` structure) peut être vide même si `S_OK` est retourné. Dans ce cas, il n’existait aucune information de recherche à retourner.

## <a name="remarks"></a>Notes
Si le `bstrVerboseSearchInfo` champ de la `MODULE_SYMBOL_SEARCH_INFO` structure n’est pas vide, il contient une liste des chemins d’accès recherchés et les résultats de cette recherche. La liste est mise en forme avec un chemin d’accès, suivi par des points de suspension (« ... »), suivi du résultat. S’il existe plus d’une paire de résultats de chemin, chaque paire est séparée par une paire « \r\n » (retour chariot/saut de seconde). Le modèle ressemble à ceci :

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Notez que la dernière entrée n’a pas de séquence \r\n.

## <a name="example"></a>Exemple
Dans cet exemple, cette méthode retourne trois chemins d’accès avec trois résultats de recherche différents. Chaque ligne se termine par une paire retour chariot/saut de ligne. L’exemple de sortie affiche simplement les résultats de la recherche sous la forme d’une chaîne unique.

> [!NOTE]
> Le résultat de l’État est tout de suite après le « ... » jusqu’à la fin de la ligne.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb... Fichier introuvable.** 
 **c:\winnt\symbols\user32.pdb... La version ne correspond pas.** 
 ** \\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Symboles chargés.**

## <a name="see-also"></a>Voir aussi

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
