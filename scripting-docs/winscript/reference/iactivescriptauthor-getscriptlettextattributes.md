---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155850"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Retourne les attributs de texte d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCode`  
 [in, size_is (`cch`)] le texte de scriptlet. Cette chaîne ne devra pas se terminer par null.  
  
 `cch`  
 [in] La taille utilisée pour le `pszCode` et `pattr` paramètres.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin de scriptlet. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur (par exemple, un double guillemet), pour détecter la fin du scriptlet. Définissez ce paramètre avec la valeur NULL si aucun délimiteur n’est utilisé pour identifier la fin du scriptlet.  
  
 `dwFlags`  
 [in] Les indicateurs qui sont associés aux attributs de texte du scriptlet. Peut être une combinaison des valeurs suivantes.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifier des identificateurs qui ont l’attribut SOURCETEXT_ATTR_IDENTIFIER et identifier les opérateurs point qui ont l’attribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifier l’objet actuel qui possède l’attribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifier le texte de contenu et le commentaire chaîne ayant l’attribut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] les informations de couleur pour le code de scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)