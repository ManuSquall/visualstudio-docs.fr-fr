---
title: 'IActiveScriptAuthor :: GetScriptletTextAttributes | Microsoft Docs'
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
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576169"
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
 [in, size_is (`cch`)] Texte scriptlet. Cette chaîne ne doit pas nécessairement se terminer par une valeur null.  
  
 `cch`  
 dans Taille utilisée pour les paramètres `pszCode` et `pattr`.  
  
 `pszDelimiter`  
 dans Adresse du délimiteur de fin de scriptlet. Lorsque `pszCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur (par exemple, deux guillemets simples) pour détecter la fin du scriptlet. Affectez la valeur NULL à ce paramètre si aucun délimiteur n’est utilisé pour identifier la fin du scriptlet.  
  
 `dwFlags`  
 dans Indicateurs associés aux attributs de texte du scriptlet. Peut être une combinaison des valeurs suivantes.  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifiez les identificateurs qui ont l’attribut SOURCETEXT_ATTR_IDENTIFIER et identifiez les opérateurs point qui ont l’attribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifiez l’objet en cours qui a l’attribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifiez le contenu de chaîne et le texte de commentaire qui a l’attribut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Informations de couleur pour le code scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor :: GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)    
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)