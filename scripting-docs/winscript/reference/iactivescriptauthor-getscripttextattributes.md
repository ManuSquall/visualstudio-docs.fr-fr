---
title: 'IActiveScriptAuthor :: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f89c7b654cc2ac7248598ee6498a3a290d17e2ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72563153"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Retourne les attributs de texte d’un bloc de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCode`  
 [in, size_is (`cch`)] Texte du bloc de script. Cette chaîne ne doit pas nécessairement se terminer par une valeur null.  
  
 `cch`  
 dans Taille utilisée pour les paramètres `pszCode` et `pattr`.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de fin de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du scriptlet. Affectez à ce paramètre la valeur NULL s’il n’existe aucun délimiteur pour identifier la fin du bloc de script.  
  
 `dwFlags`  
 dans Indicateurs associés aux attributs de texte du bloc de script. Peut être une combinaison des valeurs suivantes :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifiez les identificateurs qui ont l’attribut SOURCETEXT_ATTR_IDENTIFIER et identifiez les opérateurs point qui ont l’attribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifiez l’objet en cours qui a l’attribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifiez le contenu de chaîne et le texte de commentaire qui a l’attribut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Informations de couleur pour le code de bloc de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)