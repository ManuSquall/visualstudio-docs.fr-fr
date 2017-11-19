---
title: IActiveScriptParse32::ParseScriptText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analyse le scriptlet code donné, ajouter des déclarations dans l’espace de noms et l’évaluation du code comme il convient.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|`pstrCode`|[in] Adresse du texte scriptlet à évaluer. L’interprétation de cette chaîne varie selon le langage de script.|  
|`pstrItemName`|[in] Adresse du nom d’élément qui fournit le contexte dans lequel le scriptlet doit être évaluée. Si ce paramètre est NULL, le code est évalué dans un contexte global du moteur de script.|  
|`punkContext`|[in] Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est NULL, le moteur utilise `pstrItemName` pour identifier le contexte.|  
|`pstrDelimiter`|[in] Adresse de fin-de-scriptlet délimiteur. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le script permet de moteur dépend de l’utilisation de ces informations sur le moteur de script. Définissez ce paramètre sur `NULL` si l’ordinateur hôte n’utilisez pas un délimiteur pour marquer la fin du scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie utilisé pour le débogage.|  
|`ulStartingLineNumber`|[in] Valeur de base zéro qui spécifie la ligne à laquelle l’analyse commencera à.|  
|`dwFlags`|[in] Indicateurs associés le scriptlet. Peut être une combinaison des valeurs suivantes :|  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la distinction entre une expression de calcul et une instruction est important mais syntaxiquement ambiguë dans le langage de script, cet indicateur spécifie que le scriptlet doit être interprété comme une expression, plutôt que comme une instruction ou une liste d’instructions. Par défaut, les instructions sont supposées à moins que le bon choix peut être déterminé à partir de la syntaxe du texte scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté au cours de cet appel doit être enregistré si le moteur de script est enregistré (par exemple, via un appel à `IPersist*::Save`), ou si le moteur de script est réinitialisé par le biais d’une transition à l’état initialisé.|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par nom) en tant qu’une méthode globale dans l’espace de noms du script.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adresse d’une mémoire tampon qui reçoit les résultats du traitement du scriptlet, ou `NULL` si l’appelant n’attend aucun résultat (autrement dit, la valeur SCRIPTTEXT_ISEXPRESSION n’est pas définie).|  
|`pexcepinfo`|[out] Adresse d’une structure qui reçoit des informations sur l’exception. Cette structure est remplie si `IActiveScriptParse::ParseScriptText` retourne DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors du traitement du scriptlet. Le `pexcepinfo` paramètre contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge l’évaluation au moment de l’exécution des expressions ou des instructions.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script est dans l’état non initialisé ou fermé, ou l’indicateur SCRIPTTEXT_ISEXPRESSION a été défini et le moteur de script est dans l’état initialisé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="remarks"></a>Remarques  
 Si le moteur de script se trouve dans l’état initialisé, aucun code ne sera réellement évaluée pendant cet appel ; au lieu de cela, ce code est en file d’attente et exécuté lorsque le moteur de script est une transition dans (ou via) l’état démarré. Étant donné que l’exécution n’est pas autorisée dans l’état initialisé, il s’agit d’une erreur d’appeler cette méthode avec l’indicateur SCRIPTTEXT_ISEXPRESSION à l’état initialisé.  
  
 Le scriptlet peut être une expression, une liste d’instructions ou tout élément autorisé par le langage de script. Par exemple, cette méthode est utilisée dans l’évaluation du code HTML \<SCRIPT > balise, qui autorise des instructions être exécutée, car la page HTML est en cours de construction, au lieu de simplement les compiler à l’état de script.  
  
 Le code passé à cette méthode doit être une portion de code valide et complete. Par exemple, dans VBScript, il est non conforme pour appeler cette méthode une fois avec Sub Function et une seconde fois avec `End Sub`. L’analyseur ne doit pas attendre le deuxième appel à la fin de la sous-routine, mais au lieu de cela doit générer une erreur d’analyse, car une déclaration de la sous-routine a été démarrée mais pas terminée.  
  
 Pour plus d’informations sur les États du script, consultez la section des États de moteur de Script de [moteurs de Script Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)