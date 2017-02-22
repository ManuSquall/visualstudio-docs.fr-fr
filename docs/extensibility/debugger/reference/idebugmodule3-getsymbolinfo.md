---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "GetSymbolInfo (méthode)"
  - "IDebugModule3::GetSymbolInfo (méthode)"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère une liste de chemins d’accès aux symboles, ainsi que les résultats de recherche dans chaque chemin d’accès sont recherchés.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\] Une combinaison d’indicateurs à partir de la [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération spécifiant les champs de `pInfo` doivent être renseignés.  
  
 `pInfo`  
 \[out\] Un [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) structure dont les membres sont à remplir avec les informations spécifiées. Si cela est une valeur null, cette méthode retourne `E_INVALIDARG`.  
  
## Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`; Sinon, elle retourne un code d’erreur.  
  
> [!NOTE]
>  La chaîne retournée \(dans le `MODULE_SYMBOL_SEARCH_INFO` structure\) peut être vide même si `S_OK` est retourné. Dans ce cas, il n’a aucune information de recherche à retourner.  
  
## Notes  
 Si le `bstrVerboseSearchInfo` champ le `MODULE_SYMBOL_SEARCH_INFO` structure n’est pas vide, puis il contient une liste des chemins de recherche et les résultats de recherche. La liste est mis en forme avec un chemin d’accès, suivie de points de suspension \(«... »\), suivis par le résultat. S’il existe plusieurs paires de résultat du chemin d’accès, chaque paire est séparée par une paire \(retour chariot \/\) de « \\r\\n ». Le modèle ressemble à ceci :  
  
 \< chemin \>... \< résultat \> \\r\\n \< chemin \>... \< résultat \> \\r\\n \< chemin \>... \< résultat \>  
  
 Notez que la dernière entrée n’est pas une séquence \\r\\n.  
  
## Exemple  
 Dans cet exemple, cette méthode retourne les trois chemins d’accès avec trois résultats différents. Chaque ligne se termine par une paire retour chariot \/. L’exemple de sortie imprime simplement les résultats de recherche sous forme de chaîne unique.  
  
> [!NOTE]
>  Un résultat de l’état est tout ce qui suit immédiatement la «... » jusqu'à la fin de la ligne.  
  
```cpp#  
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
  
 **c:\\symbols\\user32.pdb... Fichier introuvable. c:\\winnt\\symbols\\user32.pdb... Version ne correspond pas. \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb... Symboles chargés.**   
## Voir aussi  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)