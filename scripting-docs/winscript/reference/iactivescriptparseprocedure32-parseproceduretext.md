---
title: IActiveScriptParseProcedure32 ::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835730"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analyse la procédure de code donnée et ajoute la procédure à l’espace de noms.  
  
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
 dans Adresse du texte de la procédure à évaluer. L’interprétation de cette chaîne dépend du langage de script.  
  
 `pstrFormalParams`  
 dans Adresse des noms de paramètres formels pour la procédure. Les noms de paramètres doivent être séparés par les délimiteurs appropriés pour le moteur de script. Les noms ne doivent pas être placés entre parenthèses.  
  
 `pstrProcedureName`  
 dans Adresse du nom de la procédure à analyser.  
  
 `pstrItemName`  
 dans Adresse du nom de l’élément qui fournit le contexte dans lequel la procédure doit être évaluée. Si ce paramètre est `NULL` , le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 dans Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où un tel contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre a `NULL` la valeur, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 dans Adresse du délimiteur de fin de procédure. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin de la procédure. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitive conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). La façon dont (et si) le moteur de script utilise ces informations dépend du moteur de script. Affectez à ce paramètre `NULL` la valeur si l’hôte n’a pas utilisé de délimiteur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 dans Valeur définie par l’application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 dans Valeur de base zéro qui spécifie la ligne à laquelle l’analyse doit commencer.  
  
 `dwFlags`  
 dans Indicateurs associés à la procédure. Peut être une combinaison de ces valeurs :  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure. Par défaut, le code peut contenir une expression, une liste d’instructions ou tout autre contenu autorisé dans une procédure par le langage de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indique que le `this` pointeur est inclus dans l’étendue de la procédure.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indique que les parents du `this` pointeur sont inclus dans l’étendue de la procédure.|  
  
 `ppdisp`  
 à Adresse du pointeur de l’objet contenant les méthodes et les propriétés globales du script. Si le moteur de script ne prend pas en charge un tel objet, `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Renvoie l'une des valeurs suivantes :  
  
|Valeur renvoyée|Signification|  
|------------------|-------------|  
|`S_OK`|Réussite.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n’est pas prise en charge. Le moteur de script ne prend pas en charge l’ajout de procédures à l’espace de noms au moment de l’exécution.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script se trouve dans l’état non initialisé ou fermé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de dispatch ; le `ppdisp` paramètre a la valeur `NULL` .|  
  
## <a name="remarks"></a>Remarques  
 Aucun code de script n’est évalué pendant cet appel ; au lieu de cela, la procédure est compilée dans l’état du script où elle peut être appelée par le script ultérieurement.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)