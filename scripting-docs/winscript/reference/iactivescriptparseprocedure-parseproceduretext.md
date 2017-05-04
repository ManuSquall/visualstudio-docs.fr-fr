---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
Analyse la procédure de code donnée et ajoute la procédure à l'espace de noms.  
  
## Syntaxe  
  
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
  
#### Paramètres  
 `pstrCode`  
 \[in\]  adresse du texte de procédure à évaluer.  La traduction de cette chaîne dépend du langage de script.  
  
 `pstrFormalParams`  
 \[in\]  Adresse les noms de paramètres formels pour la procédure.  Les noms de paramètres doivent être séparés par des séparateurs appropriés pour le moteur de script.  Les noms ne doivent pas être placés entre parenthèses.  
  
 `pstrProcedureName`  
 \[in\]  adresse du nom de procédure à analyser.  
  
 `pstrItemName`  
 \[in\]  adresse du nom d'élément qui donne le contexte dans lequel la procédure doit être évaluée.  Si ce paramètre est `NULL`, le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 \[in\]  adresse de l'objet de contexte.  Cet objet est réservé à utiliser dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d'exécution actif.  Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 \[in\]  Adresse du délimiteur de fin de la procédure.  Lorsque `pstrCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \('\), pour détecter la fin de la procédure.  Ce paramètre spécifie que le séparateur qui l'hôte utilisé, ce qui permet au moteur de script pour fournir du prétraitement primitive conditionnel \(par exemple, en remplaçant un guillemet simple \[« \] par deux guillemets simples pour l " utilisation comme séparateur\).  Exactement comment \(et\) si le moteur de script utilise ces informations dépendent du moteur de script.  Affectez à ce paramètre la `NULL` si l'hôte n'avait pas l'habitude un séparateur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 \[in\]  valeur définie par l'application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 \[in\]  La valeur de base zéro qui spécifie rayent l'analyse commence à.  
  
 `dwFlags`  
 \[in\]  Balises associées à la procédure.  Peut être une combinaison de ces valeurs :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTPROC\_ISEXPRESSION|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure.  Par défaut, le code peut contenir une expression, une liste d'instructions, ou tout autre élément autorisés dans une procédure par le langage de script.|  
|SCRIPTPROC\_IMPLICIT\_THIS|Indique que le pointeur d' `this` est inclus dans la portée de la procédure.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|Indique que les parents du pointeur d' `this` sont inclus dans la portée de la procédure.|  
  
 `ppdisp`  
 \[out\]  adresse du pointeur pour l'objet contenant les méthodes globales et les propriétés du script.  Si le moteur de script ne prend pas en charge ce type d'objet, `NULL` est retourné.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.  Le moteur de script ne prend pas en charge l'ajout de l'exécution des procédures à l'espace de noms.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script est dans l'état non initialisé ou fermé.\)|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet d'expédition ; le paramètre d' `ppdisp` a la valeur `NULL`.|  
  
## Notes  
 Aucun code de script n'est évalué pendant cet appel ; au contraire, la procédure est compilée dans l'état de script où elle peut être appelée par le script ultérieurement.  
  
## Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)