---
title: IActiveScriptParseProcedure::ParseProcedureText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analyse de la procédure de code donnée et ajoute la procédure à l’espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Adresse du texte de la procédure à évaluer. L’interprétation de cette chaîne varie selon le langage de script.  
  
 `pstrFormalParams`  
 [in] Adresse du nom de paramètre formel pour la procédure. Les noms de paramètres doivent être séparés par les délimiteurs appropriés pour le moteur de script. Les noms ne doivent pas être placées entre parenthèses.  
  
 `pstrProcedureName`  
 [in] Adresse du nom de la procédure doit être analysé.  
  
 `pstrItemName`  
 [in] Adresse du nom d’élément qui fournit le contexte dans lequel la procédure doit être évaluée. Si ce paramètre est `NULL`, l’évaluation du code dans un contexte global du moteur de script.  
  
 `punkContext`  
 [in] Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 [in] Adresse du délimiteur de fin de la procédure. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin de la procédure. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le script permet de moteur dépend de l’utilisation de ces informations sur le moteur de script. Définissez ce paramètre sur `NULL` si l’ordinateur hôte n’utilisez pas un délimiteur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 [in] Valeur définie par l’application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 [in] Valeur de base zéro qui spécifie la ligne à laquelle l’analyse commencera à.  
  
 `dwFlags`  
 [in] Indicateurs associés à la procédure. Peut être une combinaison des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure. Par défaut, le code peut contenir une expression, une liste d’instructions ou tout autre autorisé dans une procédure par le langage de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indique que le `this` pointeur est inclus dans l’étendue de la procédure.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indique que les parents de le `this` pointeur sont inclus dans l’étendue de la procédure.|  
  
 `ppdisp`  
 [out] Adresse du pointeur de l’objet qui contient des méthodes globales et les propriétés du script. Si le moteur de script ne prend pas en charge un tel objet `NULL` est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge l’ajout d’exécution des procédures pour l’espace de noms.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script est dans l’état non initialisé ou fermé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet de distribution ; le `ppdisp` paramètre est défini sur `NULL`.|  
  
## <a name="remarks"></a>Remarques  
 Aucun code de script n’est évaluée pendant cet appel ; au lieu de cela, la procédure est compilée à l’état de script où il peut être appelé par le script ultérieurement.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)