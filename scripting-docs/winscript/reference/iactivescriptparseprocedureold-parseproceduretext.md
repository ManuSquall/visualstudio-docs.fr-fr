---
title: IActiveScriptParseProcedureOld ::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577450"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analyse la procédure de code donnée et ajoute une procédure anonyme à l’espace de noms.  
  
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
 dans Texte de la procédure à évaluer. L’interprétation de cette chaîne dépend du langage de script.  
  
 `pstrFormalParams`  
 dans Noms de paramètres formels pour la procédure. Les noms de paramètres doivent être séparés par les délimiteurs appropriés pour le moteur de script. Les noms ne doivent pas être placés entre parenthèses.  
  
 `pstrItemName`  
 dans Nom de l’élément nommé qui donne le contexte dans lequel la procédure doit être évaluée. Si ce paramètre est `NULL`, le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 dans Objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où un tel contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 dans Délimiteur de fin de procédure. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin de la procédure. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitives conditionnelles (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations dépend du moteur de script. Définissez ce paramètre sur `NULL` si l’hôte n’a pas utilisé de délimiteur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 dans Valeur définie par l’application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 dans Valeur de base zéro qui spécifie la ligne sur laquelle l’analyse doit commencer.  
  
 `dwFlags`  
 dans Indicateurs associés à la procédure. Peut être une combinaison de ces valeurs.  
  
|Constante|valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indique que le code de `pstrCode` est une expression qui représente la valeur de retour de la procédure.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indique que le pointeur de `this` est inclus dans l’étendue de la procédure.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indique que les parents du pointeur `this` sont inclus dans l’étendue de la procédure.|  
  
 `ppdisp`  
 à Retourne un wrapper de dispatch où la méthode par défaut est la procédure analysée par cette méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge l’ajout de procédures à l’espace de noms au moment de l’exécution.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script se trouve dans l’état non initialisé ou fermé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de dispatch ; la `ppdisp`parameter est définie sur `NULL`.|  
  
## <a name="remarks"></a>Notes  
 Aucun code de script n’est évalué pendant cet appel ; au lieu de cela, la procédure est compilée dans une méthode sur `ppdisp` où elle peut être appelée par le script ultérieurement.  
  
 Cette interface est déconseillée en faveur de l’interface `IActiveScriptParseProcedure`. La méthode `IActiveScriptParseProcedure::ParseProcedureText` est semblable à cette méthode, mais elle permet de spécifier le nom de la procédure. Dans toutes les circonstances, `IActiveScriptParseProcedure::ParseProcedureText` doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)  
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)