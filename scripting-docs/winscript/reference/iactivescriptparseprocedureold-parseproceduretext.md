---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e521bbdcd8d7397c1c2dfb377fd9b41811499f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993213"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analyse de la procédure de code donné et ajoute une procédure anonyme à l’espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrCode`  
 [in] Le texte de la procédure à évaluer. L’interprétation de cette chaîne varie selon le langage de script.  
  
 `pstrFormalParams`  
 [in] Noms de paramètres formels de la procédure. Les noms de paramètres doivent être séparées avec les délimiteurs appropriés pour le moteur de script. Les noms ne doivent pas être placées entre parenthèses.  
  
 `pstrItemName`  
 [in] Le nom de l’élément nommé qui fournit le contexte dans lequel la procédure doit être évaluée. Si ce paramètre est `NULL`, le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 [in] L’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 [in] Le délimiteur de fin de la procédure. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les deux guillemets («), pour détecter la fin de la procédure. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script fournir certains conditionnelles, prétraitement primitif (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur script utilise ces informations varient selon le moteur de script. Définissez ce paramètre sur `NULL` si l’hôte n’utilisez pas un séparateur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 [in] Valeur définie par l’application qui est utilisée pour le débogage.  
  
 `ulStartingLineNumber`  
 [in] Valeur de base zéro qui spécifie la ligne à laquelle l’analyse commence.  
  
 `dwFlags`  
 [in] Indicateurs associés à la procédure. Peut être une combinaison de ces valeurs.  
  
|Constante|Value|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indique que le `this` pointeur est inclus dans le cadre de la procédure.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indique que les parents de la `this` pointeur sont inclus dans le cadre de la procédure.|  
  
 `ppdisp`  
 [out] Retourne un wrapper de dispatch où la méthode par défaut est la procédure analysée par cette méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge l’ajout d’exécution des procédures pour l’espace de noms.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script est dans un état non initialisé ou fermé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de répartition ; le `ppdisp`paramètre est défini sur `NULL`.|  
  
## <a name="remarks"></a>Notes  
 Aucun code de script n’est évalué pendant cet appel ; au lieu de cela, la procédure est compilée dans une méthode sur `ppdisp` où elle peut être appelée par le script ultérieurement.  
  
 Cette interface est déconseillée en faveur de la `IActiveScriptParseProcedure` interface. Le `IActiveScriptParseProcedure::ParseProcedureText` méthode est similaire à cette méthode, mais il permet de spécifier le nom de procédure. Dans tous les cas, `IActiveScriptParseProcedure::ParseProcedureText` doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedureOld (Interface)](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)