---
title: IActiveScriptParse::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3396aee8c044ee9b84d7d6256c6ad69a99965170
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158865"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analyse le scriptlet de code donné, ajoutant des déclarations dans l’espace de noms et l’évaluation de code comme il convient.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|`pstrCode`|[in] Adresse du texte de scriptlet à évaluer. L’interprétation de cette chaîne varie selon le langage de script.|  
|`pstrItemName`|[in] Adresse du nom d’élément qui fournit le contexte dans lequel le scriptlet doit être évaluée. Si ce paramètre est NULL, le code est évalué dans le contexte global du moteur de script.|  
|`punkContext`|[in] Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où ce contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre est NULL, le moteur utilise `pstrItemName` pour identifier le contexte.|  
|`pstrDelimiter`|[in] Adresse du délimiteur de fin de scriptlet. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les deux guillemets («), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script fournir un prétraitement primitif conditionnel (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations varie selon le moteur de script. Définissez ce paramètre sur `NULL` si l’hôte n’utilisez pas un séparateur pour marquer la fin du scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie utilisé pour le débogage.|  
|`ulStartingLineNumber`|[in] Valeur de base zéro qui spécifie la ligne qui commence à l’analyse.|  
|`dwFlags`|[in] Indicateurs associés au scriptlet. Peut être une combinaison des valeurs suivantes :|  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la distinction entre une expression de calcul et une instruction est importante mais syntaxiquement ambiguë dans le langage de script, cet indicateur spécifie que le scriptlet doit être interprétée comme une expression, plutôt que comme une instruction ou une liste d’instructions. Par défaut, les instructions sont assumées sauf si le choix correct peut être déterminé à partir de la syntaxe du texte de scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté pendant cet appel doit être enregistré si le moteur de script est enregistré (par exemple, via un appel à `IPersist*::Save`), ou si le moteur de script est réinitialisé via une transition vers l’état initialisé.|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par nom) en tant qu’une méthode globale dans l’espace de noms du script.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adresse d’une mémoire tampon qui reçoit les résultats du traitement du scriptlet, ou `NULL` si l’appelant n’attend aucun résultat (autrement dit, la valeur SCRIPTTEXT_ISEXPRESSION n’est pas définie).|  
|`pexcepinfo`|[out] Adresse d’une structure qui reçoit des informations sur les exceptions. Cette structure est remplie si `IActiveScriptParse::ParseScriptText` retourne DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors du traitement du scriptlet. Le `pexcepinfo` paramètre contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge. Le moteur de script ne prend pas en charge la version d’évaluation de l’exécution d’expressions ou instructions.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script est dans un état non initialisé ou fermé, ou l’indicateur SCRIPTTEXT_ISEXPRESSION était défini et le moteur de script est dans l’état initialisé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="remarks"></a>Notes  
 Si le moteur de script est dans l’état initialisé, aucun code n’est réellement évalué pendant cet appel ; au lieu de cela, ce code est en file d’attente et exécuté lorsque le moteur de script est une transition dans (ou via) l’état démarré. Étant donné que l’exécution n’est pas autorisée dans l’état initialisé, il est une erreur d’appeler cette méthode avec l’indicateur SCRIPTTEXT_ISEXPRESSION lorsqu’il est dans l’état initialisé.  
  
 Le scriptlet peut être une expression, une liste d’instructions ou tout élément autorisé par le langage de script. Par exemple, cette méthode est utilisée dans l’évaluation du code HTML \<SCRIPT > balise, qui autorise des instructions à exécuter comme la page HTML est en cours de construction, au lieu de les compiler dans l’état du script.  
  
 Le code passé à cette méthode doit être une portion de code valide et complete. Par exemple, dans VBScript, il est illégal d’appeler cette méthode une fois avec Sub Function (x) et ensuite une deuxième fois avec `End Sub`. L’analyseur ne doit pas attendre le deuxième appel à terminer la sous-routine, mais doit générer une erreur d’analyse, car une déclaration de sous-routine a été démarrée mais pas terminée.  
  
 Pour plus d’informations sur les États de script, consultez la section d’états de moteur de Script de [moteurs de Script Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)