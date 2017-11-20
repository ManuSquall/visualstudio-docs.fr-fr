---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Retourne les attributs de texte d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in, size_is (`cch`)] le texte scriptlet. Cette chaîne n’est pas à se terminer par null.  
  
 `cch`  
 [in] La taille utilisée pour la `pszCode` et `pattr` paramètres.  
  
 `pszDelimiter`  
 [in] L’adresse de fin-de-scriptlet délimiteur. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples), pour détecter la fin du scriptlet. Définissez ce paramètre avec la valeur NULL si aucun délimiteur n’est utilisé pour identifier la fin du scriptlet.  
  
 `dwFlags`  
 [in] Indicateurs qui sont associés aux attributs de texte du scriptlet. Peut être une combinaison des valeurs suivantes.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identifier des identificateurs qui ont l’attribut SOURCETEXT_ATTR_IDENTIFIER et identifier les opérateurs point qui ont l’attribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0 x 0100|Identifier l’objet actuel qui possède l’attribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identifier le texte de commentaire et de contenu chaîne qui a l’attribut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [dans, du délai d’attente, size_is (`cch`)] les informations de couleur pour le code scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)