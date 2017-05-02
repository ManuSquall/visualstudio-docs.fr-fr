---
title: "IActiveScriptParse::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_ParseScriptText"
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptParse::ParseScriptText
Analyse le scriptlet de code donné, en ajoutant des déclarations dans l'espace de noms et en évaluant le code si nécessaire.  
  
## Syntaxe  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### Paramètres  
  
|||  
|-|-|  
|`pstrCode`|\[in\] Adresse du texte de scriptlet à évaluer.  L'interprétation de cette chaîne dépend du langage de script.|  
|`pstrItemName`|\[in\] Adresse du nom d'élément qui fournit le contexte d'évaluation du scriptlet.  Si ce paramètre a la valeur Null, le code est évalué dans le contexte global du moteur de script.|  
|`punkContext`|\[in\] Adresse de l'objet de contexte.  Cet objet est réservé pour être utilisé dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d'exécution actif.  Si ce paramètre a la valeur null, le moteur utilise `pstrItemName` pour identifier le contexte.|  
|`pstrDelimiter`|\[in\] Adresse du délimiteur de fin de scriptlet.  Lorsque `pstrCode` est analysé à partir d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \("\), pour détecter la fin du scriptlet.  Ce paramètre spécifie le séparateur que l'hôte a utilisé, permettant au moteur de script de fournir un prétraitement primitif conditionnel \(par exemple, en remplaçant un guillemet simple \['\] par deux guillemets simples à utiliser comme séparateur\).  La façon dont le moteur de script utilise ces informations dépend de celui\-ci.  Affectez à ce paramètre la valeur `NULL` si l'hôte n'utilisait pas un séparateur pour marquer la fin du scriptlet.|  
|`dwSourceContextCookie`|\[in\] Cookie utilisé à des fins de débogage.|  
|`ulStartingLineNumber`|\[in\] Valeur de base zéro qui spécifie la ligne où commence l'analyse.|  
|`dwFlags`|\[in\] Indicateurs associés au scriptlet.  Il peut s'agir d'une combinaison de ces valeurs :|  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTTEXT\_ISEXPRESSION|Si la distinction entre une expression de calcul et une instruction est importante mais syntaxiquement ambiguë dans le langage de script, cet indicateur spécifie que le scriptlet doit être interprété comme une expression, plutôt que comme une instruction ou une liste d'instructions.  Par défaut, les instructions sont assumées sauf si le choix correct peut être déterminé à partir de la syntaxe du texte de scriptlet.|  
|SCRIPTTEXT\_ISPERSISTENT|Indique que le code ajouté pendant cet appel doit être enregistré si le moteur de script est enregistré \(par exemple, via un appel à `IPersist*::Save`\), ou si le moteur de script est réinitialisé via une transition vers l'état initialisé.|  
|SCRIPTTEXT\_ISVISIBLE|Indique que le texte du script doit être visible \(et, par conséquent, peut être appelé par nom\) en tant que méthode globale dans l'espace de noms du script.|  
  
|||  
|-|-|  
|`pvarResult`|\[out\] Adresse d'une mémoire tampon qui reçoit les résultats du traitement du scriptlet, ou `NULL` si l'appelant n'attend aucun résultat \(autrement dit, si la valeur de SCRIPTTEXT\_ISEXPRESSION n'est pas définie\).|  
|`pexcepinfo`|\[out\] Adresse d'une structure qui reçoit des informations sur les exceptions.  Cette structure est remplie si `IActiveScriptParse::ParseScriptText` retourne DISP\_E\_EXCEPTION.|  
  
## Valeur de retour  
 Retourne l'une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`DISP_E_EXCEPTION`|Une exception s'est produite lors du traitement du scriptlet.  Le paramètre `pexcepinfo` contient des informations sur l'exception.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Le pointeur spécifié est incorrect.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.  Le moteur de script ne prend pas en charge l'évaluation au moment de l'exécution des expressions ou des instructions.|  
|`E_UNEXPECTED`|L'appel n'était pas prévu \(par exemple, le moteur de script se trouve dans un état non initialisé ou fermé, ou l'indicateur SCRIPTTEXT\_ISEXPRESSION était défini et le moteur de script se trouve dans un état initialisé\).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s'est produite dans le scriptlet.|  
  
## Notes  
 Si le moteur de script se trouve dans l'état initialisé, aucun code n'est réellement évalué pendant cet appel ; en revanche, ce code est mis en file d'attente et exécuté lorsque le moteur de script passe dans l'état démarré.  Étant donné que l'exécution n'est pas autorisée dans l'état initialisé, c'est une erreur d'appeler cette méthode avec l'indicateur SCRIPTTEXT\_ISEXPRESSION lorsqu'elle se trouve à l'état initialisé.  
  
 Le scriptlet peut être une expression, une liste d'instructions, ou tout élément autorisé par le langage de script.  Par exemple, cette méthode est utilisée dans l'évaluation de la balise HTML \<SCRIPT\>, qui autorise l'exécution d'instructions pendant la construction de la page HTML, au lieu de les compiler dans l'état du script.  
  
 Le code passé à cette méthode doit être une partie de code valide et complète.  Par exemple, dans VBScript, il est illégal d'appeler cette méthode une fois avec Sub Function\(x\) puis une deuxième fois avec `End Sub`.  L'analyseur ne doit pas attendre le deuxième appel pour terminer la sous\-routine, mais doit générer une erreur d'analyse car une déclaration de sous\-routine a été démarrée mais ne s'est pas terminée.  
  
 Pour plus d'informations sur les états de script, consultez la section États du moteur de script de [Windows Script, moteurs](../../winscript/windows-script-engines.md).  
  
## Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)