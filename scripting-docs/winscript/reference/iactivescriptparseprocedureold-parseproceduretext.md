---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
Analyse la procédure de code donnée et ajoute une procédure anonyme à l'espace de noms.  
  
## Syntaxe  
  
```  
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
  
#### Paramètres  
 `pstrCode`  
 \[in\]  le texte de procédure à évaluer.  La traduction de cette chaîne dépend du langage de script.  
  
 `pstrFormalParams`  
 \[in\]  Noms de paramètres formels pour la procédure.  Les noms de paramètres doivent être séparés par des séparateurs appropriés pour le moteur de script.  Les noms ne doivent pas être placés entre parenthèses.  
  
 `pstrItemName`  
 \[in\]  le nom de l'élément nommé qui donne le contexte dans lequel la procédure doit être évaluée.  Si ce paramètre est `NULL`, le code est évalué dans le contexte global du moteur de script.  
  
 `punkContext`  
 \[in\]  l'objet de contexte.  Cet objet est réservé à utiliser dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d'exécution actif.  Si ce paramètre est `NULL`, le moteur utilise `pstrItemName` pour identifier le contexte.  
  
 `pstrDelimiter`  
 \[in\]  Délimiteur de fin de la procédure.  Lorsque `pstrCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \('\), pour détecter la fin de la procédure.  Ce paramètre spécifie que le séparateur qui l'hôte utilisé, ce qui permet au moteur de script pour fournir du prétraitement conditionnel et primitif \(par exemple, en remplaçant un guillemet simple \[« \] par deux guillemets simples pour l " utilisation comme séparateur\).  Exactement comment \(et\) si le moteur de script utilise ces informations dépendent du moteur de script.  Affectez à ce paramètre la `NULL` si l'hôte n'avait pas l'habitude un séparateur pour marquer la fin de la procédure.  
  
 `dwSourceContextCookie`  
 \[in\]  valeur définie par l'application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 \[in\]  Valeur de base zéro qui spécifie la ligne l'analyse démarre.  
  
 `dwFlags`  
 \[in\]  Balises associées à la procédure.  Peut être une combinaison de ces valeurs.  
  
|Constante|Valeur|Signification|  
|---------------|------------|-------------------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|Indique que le code dans `pstrCode` est une expression qui représente la valeur de retour de la procédure.|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|Indique que le pointeur d' `this` est inclus dans la portée de la procédure.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|Indique que les parents du pointeur d' `this` sont inclus dans la portée de la procédure.|  
  
 `ppdisp`  
 \[out\]  Retourne un wrapper d'expédition où la méthode par défaut est la procédure analysées par cette méthode.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.  Le moteur de script ne prend pas en charge l'ajout de l'exécution des procédures à l'espace de noms.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script est dans l'état non initialisé ou fermé.\)|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée produite dans la procédure.|  
|`S_FALSE`|Le moteur de script ne prend pas en charge un objet d'expédition ; le paramètre d' `ppdisp`a la valeur `NULL`.|  
  
## Notes  
 Aucun code de script n'est évalué pendant cet appel ; au contraire, la procédure est compilée dans une méthode sur `ppdisp` où elle peut être appelée par le script ultérieurement.  
  
 Cette interface est déconseillée en faveur de l'interface d' `IActiveScriptParseProcedure` .  La méthode d' `IActiveScriptParseProcedure::ParseProcedureText` est semblable à cette méthode, mais elle permet le nom de procédure à spécifier.  Dans toutes les circonstances, `IActiveScriptParseProcedure::ParseProcedureText` doit être utilisé.  
  
## Voir aussi  
 [IActiveScriptParseProcedureOld, interface](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)