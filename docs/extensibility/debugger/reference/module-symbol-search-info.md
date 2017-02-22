---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "Structure MODULE_SYMBOL_SEARCH_INFO"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contient des informations d’état sur les chemins de recherche de symbole qui a été effectuée dans.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwValidFields`  
 Une combinaison d’indicateurs à partir de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération spécifiant le type d’informations de recherche décrits dans cette structure.  
  
 `bstrVerboseSearchInfo`  
 Chemin de recherche et les résultats concaténés en une chaîne unique.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est retournée à partir d’un appel à la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) (méthode).  
  
 Si le `bstrVerboseSearchInfo` champ n’est pas vide, alors qu’il contient une liste des chemins de recherche et les résultats de recherche. La liste est mis en forme avec un chemin d’accès, suivie de points de suspension («... »), suivis par le résultat. S’il existe plusieurs paires de résultat du chemin d’accès, chaque paire est séparée par une paire (retour chariot /) de « \r\n ». Le modèle ressemble à ceci :  
  
 \< chemin d’accès>... \< résultat>\r\n \< chemin d’accès>... \< résultat>\r\n \< chemin d’accès>... \< résultat>  
  
 Notez que la dernière entrée n’est pas une séquence \r\n.  
  
 Voici une éventuelle `bstrVerboseSearchInfo` chaîne qui a été envoyé vers la sortie standard.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)