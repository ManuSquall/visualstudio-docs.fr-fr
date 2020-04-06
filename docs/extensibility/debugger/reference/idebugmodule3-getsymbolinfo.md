---
title: IDebugModule3::GetSymbolInfo - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726893"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Récupère une liste de chemins qui sont recherchés pour les symboles ainsi que les résultats de la recherche de chaque chemin.

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
[dans] Une combinaison de drapeaux de [l’SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération précisant quels champs de `pInfo` sont à remplir.

`pInfo`\
[out] Une [structure MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) dont les membres doivent être remplis avec les informations spécifiées. S’il s’agit d’une valeur nulle, cette méthode revient `E_INVALIDARG`.

## <a name="return-value"></a>Valeur de retour
Si la méthode réussit, elle revient `S_OK`; autrement, il renvoie un code d’erreur.

> [!NOTE]
> La ficelle retournée `MODULE_SYMBOL_SEARCH_INFO` (dans la structure) `S_OK` pourrait être vide même si elle est retournée. En l’espèce, il n’y avait aucune information de recherche à retourner.

## <a name="remarks"></a>Notes
Si `bstrVerboseSearchInfo` le champ `MODULE_SYMBOL_SEARCH_INFO` de la structure n’est pas vide, alors il contient une liste de chemins recherchés et les résultats de cette recherche. La liste est formatée avec un chemin, suivi d’une ellipsis ("..."), suivie par le résultat. S’il y a plus d’une paire de résultats de chemin, alors chaque paire est séparée par une paire de « r’n » (carriage-return/linefeed). Le modèle ressemble à ceci:

\<chemin>... \<résultat>\<chemin>... \<résultat>\<chemin>... \<résultat>

Notez que la dernière entrée n’a pas de séquence de r’n.

## <a name="example"></a>Exemple
Dans cet exemple, cette méthode renvoie trois voies avec trois résultats de recherche différents. Chaque ligne est terminée avec une paire de transport-retour/linefeed. La sortie d’exemple imprime simplement les résultats de recherche comme une seule chaîne.

> [!NOTE]
> Un résultat de statut est tout immédiatement après le "..." jusqu’à la fin de la ligne.

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

**c: -symboles32.pdb... Fichier non trouvé.** 
 **c : symboles de winnt32.pdb... La version ne correspond pas.** 
 ** \\Symboles32.dll.dll.dll.dll.dll-0a8sd0ad8ad.user32.pdb... Symboles chargés.**

## <a name="see-also"></a>Voir aussi

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
