---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9deadc13f8cbe3678282bb2d9ac619959ecd26b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875916"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Contient des informations d’état sur les chemins de recherche de symbole qui a été effectuée dans.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `dwValidFields`  
 Une combinaison d’indicateurs de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) énumération spécifiant le type d’information de recherche décrit dans cette structure.  
  
 `bstrVerboseSearchInfo`  
 Chemin de recherche et les résultats concaténés en une seule chaîne.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée à partir d’un appel à la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) (méthode).  
  
 Si le `bstrVerboseSearchInfo` champ n’est pas vide, puis il contient une liste de chemins de recherche et les résultats de cette recherche. La liste est mis en forme avec un chemin d’accès, suivie de points de suspension («... »), suivi par le résultat. S’il existe plusieurs paires de résultat de chemin d’accès, chaque paire est séparée par une paire (retour chariot /) de « \r\n ». Le modèle ressemble à ceci :  
  
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