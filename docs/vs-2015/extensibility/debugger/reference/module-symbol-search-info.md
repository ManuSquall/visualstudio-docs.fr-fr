---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
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
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 074e837a1c0449420d7042539fb4c8dfa0396fe6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504811"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [MODULE_SYMBOL_SEARCH_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-symbol-search-info).  
  
Contient des informations d’état sur les chemins de recherche de symbole qui a été effectuée dans.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Paramètres  
 `dwValidFields`  
 Une combinaison d’indicateurs de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération spécifiant le type d’information de recherche décrit dans cette structure.  
  
 `bstrVerboseSearchInfo`  
 Chemin de recherche et les résultats concaténés en une seule chaîne.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée à partir d’un appel à la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) (méthode).  
  
 Si le `bstrVerboseSearchInfo` champ n’est pas vide, puis il contient une liste de chemins de recherche et les résultats de cette recherche. La liste est mis en forme avec un chemin d’accès, suivie de points de suspension («... »), suivis par le résultat. S’il existe plusieurs paires de résultat de chemin d’accès, chaque paire est séparée par une paire (retour chariot /) de « \r\n ». Le modèle ressemble à ceci :  
  
 \<chemin d’accès >... \<résultat > \r\n\<chemin d’accès >... \<résultat > \r\n\<chemin d’accès >... \<résultat >  
  
 Notez que la dernière entrée n’est pas une séquence \r\n.  
  
 Voici un éventuel `bstrVerboseSearchInfo` chaîne qui a été envoyé vers une sortie standard.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

