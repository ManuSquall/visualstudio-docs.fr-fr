---
title: IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 57513e51248e26e39f95871e0dad329e8cc2f82c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094703"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc de script.  
  
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
 [in, size_is (`cch`)] le texte du bloc de script. Cette chaîne ne devra pas se terminer par null.  
  
 `cch`  
 [in] La taille utilisée pour le `pszCode` et `pattr` paramètres.  
  
 `pszDelimiter`  
 [in] L’adresse du délimiteur de fin de script. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur (par exemple, un double guillemet), pour détecter la fin du scriptlet. Définissez ce paramètre avec la valeur NULL s’il n’existe pas de séparateurs pour identifier la fin du bloc de script.  
  
 `dwFlags`  
 [in] Les indicateurs qui sont associés aux attributs de texte du bloc de script. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identifier des identificateurs qui ont l’attribut SOURCETEXT_ATTR_IDENTIFIER et identifier les opérateurs point qui ont l’attribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifier l’objet actuel qui possède l’attribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identifier le texte de contenu et le commentaire chaîne ayant l’attribut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] les informations de couleur pour le code de bloc de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)