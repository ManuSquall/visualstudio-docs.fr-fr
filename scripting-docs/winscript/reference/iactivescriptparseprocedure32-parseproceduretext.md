---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993395"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analyse de la procédure de code donné et ajoute la procédure à l’espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrCode`  
 [in] Adresse du texte de procédure à évaluer. L’interprétation de cette chaîne varie selon le langage de script.  
  
 `pstrFormalParams`  
 [in] Adresse du nom de paramètre formel pour la procédure. Les noms de paramètres doivent être séparées avec les délimiteurs appropriés pour le moteur de script. Les noms ne doivent pas être placées entre parenthèses.  
  
 `pstrProcedureName`  
 [in] Adresse du nom de la procédure à analyser.  
  
 `pstrItemName`  
 [in] Adresse du nom d’élément qui fournit le contexte dans lequel la procédure doit être évaluée. Si ce paramètre est `NULL`, le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 [in] Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 [in] Adresse du délimiteur de fin de la procédure. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les deux guillemets («), pour détecter la fin de la procédure. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script fournir un prétraitement primitif conditionnel (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations varie selon le moteur de script. Définissez ce paramètre sur `NULL` si l’hôte n’utilisez pas un séparateur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 [in] Valeur définie par l’application qui est utilisée pour le débogage.  
  
 `ulStartingLineNumber`  
 [in] Valeur de base zéro qui spécifie la ligne qui commence à l’analyse.  
  
 `dwFlags`  
 [in] Indicateurs associés à la procédure. Peut être une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure. Par défaut, le code peut contenir une expression, une liste d’instructions ou tout élément else autorisé dans une procédure par le langage de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indique que le `this` pointeur est inclus dans le cadre de la procédure.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indique que les parents de la `this` pointeur sont inclus dans le cadre de la procédure.|  
  
 `ppdisp`  
 [out] Adresse du pointeur de l’objet contenant les méthodes globales et les propriétés du script. Si le moteur de script ne prend pas en charge ce type d’objet `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge l’ajout d’exécution des procédures pour l’espace de noms.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script est dans un état non initialisé ou fermé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de répartition ; le `ppdisp` paramètre est défini sur `NULL`.|  
  
## <a name="remarks"></a>Notes  
 Aucun code de script n’est évalué pendant cet appel ; au lieu de cela, la procédure est compilée à l’état du script où elle peut être appelée par le script ultérieurement.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)