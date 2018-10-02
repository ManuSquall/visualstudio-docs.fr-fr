---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0caac78e53e9b02fde43a45e32fdff28d6b87e6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494427"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugModule3::GetSymbolInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule3-getsymbolinfo).  
  
Récupère une liste de chemins d’accès qui sont explorés pour les symboles, ainsi que les résultats de recherche dans chaque chemin d’accès.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 [in] Une combinaison d’indicateurs de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération spécifiant les champs de `pInfo` doivent être renseignés.  
  
 `pInfo`  
 [out] Un [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) structure dont les membres sont à remplir avec les informations spécifiées. Si c’est une valeur null, cette méthode retourne `E_INVALIDARG`.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`; sinon, elle retourne un code d’erreur.  
  
> [!NOTE]
>  La chaîne retournée (dans le `MODULE_SYMBOL_SEARCH_INFO` structure) peut être vide même si `S_OK` est retourné. Dans ce cas, il n’a aucune information de recherche à retourner.  
  
## <a name="remarks"></a>Notes  
 Si le `bstrVerboseSearchInfo` champ la `MODULE_SYMBOL_SEARCH_INFO` structure n’est pas vide, puis il contient une liste de chemins de recherche et les résultats de cette recherche. La liste est mis en forme avec un chemin d’accès, suivie de points de suspension («... »), suivis par le résultat. S’il existe plusieurs paires de résultat de chemin d’accès, chaque paire est séparée par une paire (retour chariot /) de « \r\n ». Le modèle ressemble à ceci :  
  
 \<chemin d’accès >... \<résultat > \r\n\<chemin d’accès >... \<résultat > \r\n\<chemin d’accès >... \<résultat >  
  
 Notez que la dernière entrée n’est pas une séquence \r\n.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, cette méthode retourne les trois chemins d’accès avec trois résultats de recherche différente. Chaque ligne se termine par une paire retour chariot /. L’exemple de sortie imprime simplement les résultats de recherche sous forme de chaîne unique.  
  
> [!NOTE]
>  Un résultat d’état est tout ce qui suit immédiatement la «... » jusqu'à la fin de la ligne.  
  
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
  
 **c:\symbols\user32.pdb... Fichier introuvable.**  
**c:\winnt\symbols\user32.pdb... Version ne correspond pas.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symboles chargés.**   
## <a name="see-also"></a>Voir aussi  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

