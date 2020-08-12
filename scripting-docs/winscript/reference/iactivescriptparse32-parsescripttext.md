---
title: IActiveScriptParse32 ::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9fd497dcda7e40cf0dbe6409193019ddae84c80b
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144400"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analyse le scriptlet de code donné, en ajoutant des déclarations dans l’espace de noms et en évaluant le code comme il convient.  
  
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
  
| Paramètre | Description |  
|-|-|  
|`pstrCode`|dans Adresse du texte scriptlet à évaluer. L’interprétation de cette chaîne dépend du langage de script.|  
|`pstrItemName`|dans Adresse du nom de l’élément qui fournit le contexte dans lequel le scriptlet doit être évalué. Si ce paramètre a la valeur NULL, le code est évalué dans le contexte global du moteur de script.|  
|`punkContext`|dans Adresse de l’objet de contexte. Cet objet est réservé pour une utilisation dans un environnement de débogage, où un tel contexte peut être fourni par le débogueur pour représenter un contexte d’exécution actif. Si ce paramètre a la valeur NULL, le moteur utilise `pstrItemName` pour identifier le contexte.|  
|`pstrDelimiter`|dans Adresse du délimiteur de fin de scriptlet. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitive conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). La façon dont (et si) le moteur de script utilise ces informations dépend du moteur de script. Affectez à ce paramètre `NULL` la valeur si l’hôte n’a pas utilisé de délimiteur pour marquer la fin du scriptlet.|  
|`dwSourceContextCookie`|dans Cookie utilisé à des fins de débogage.|  
|`ulStartingLineNumber`|dans Valeur de base zéro qui spécifie la ligne à laquelle l’analyse doit commencer.|  
|`dwFlags`|dans Indicateurs associés au scriptlet. Peut être une combinaison de ces valeurs :|  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la distinction entre une expression de calcul et une instruction est importante mais syntaxiquement ambiguë dans le langage de script, cet indicateur spécifie que le scriptlet doit être interprété comme une expression, et non comme une instruction ou une liste d’instructions. Par défaut, les instructions sont supposées, sauf si le choix correct peut être déterminé à partir de la syntaxe du texte scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté au cours de cet appel doit être enregistré en cas d’enregistrement du moteur de script (par exemple, via un appel à `IPersist*::Save` ), ou si le moteur de script est réinitialisé par le biais d’une transition vers l’état initialisé.|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par son nom) en tant que méthode globale dans l’espace de noms du script.|  
  
| Paramètre | Description |  
|-|-|  
|`pvarResult`|à Adresse d’une mémoire tampon qui reçoit les résultats du traitement du scriptlet, ou `NULL` si l’appelant n’attend aucun résultat (autrement dit, la valeur SCRIPTTEXT_ISEXPRESSION n’est pas définie).|  
|`pexcepinfo`|à Adresse d’une structure qui reçoit des informations sur l’exception. Cette structure est remplie si `IActiveScriptParse::ParseScriptText` retourne DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valeur de retour  
 Renvoie l'une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Réussite.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors du traitement du scriptlet. Le `pexcepinfo` paramètre contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_NOTIMPL`|Cette méthode n’est pas prise en charge. Le moteur de script ne prend pas en charge l’évaluation au moment de l’exécution d’expressions ou d’instructions.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script se trouve dans l’état non initialisé ou fermé, ou l’indicateur de SCRIPTTEXT_ISEXPRESSION a été défini et le moteur de script est dans l’état initialisé).|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="remarks"></a>Notes  
 Si le moteur de script se trouve dans l’État Initialized, aucun code n’est réellement évalué pendant cet appel ; au lieu de cela, ce code est mis en file d’attente et exécuté lorsque le moteur de script passe dans l’état Démarré (ou jusqu’à). Étant donné que l’exécution n’est pas autorisée dans l’État Initialized, c’est une erreur d’appeler cette méthode avec l’indicateur SCRIPTTEXT_ISEXPRESSION lorsque l’État est initialisé.  
  
 Le scriptlet peut être une expression, une liste d’instructions ou tout ce qui est autorisé par le langage de script. Par exemple, cette méthode est utilisée dans l’évaluation de la \<SCRIPT> balise HTML, qui permet d’exécuter des instructions au fur et à mesure de la construction de la page HTML, au lieu de les compiler uniquement dans l’état du script.  
  
 Le code passé à cette méthode doit être une partie de code valide et complète. Par exemple, dans VBScript, il est illégal d’appeler cette méthode une fois avec la fonction Sub (x), puis une deuxième fois avec `End Sub` . L’analyseur ne doit pas attendre que le deuxième appel termine la sous-routine, mais doit générer une erreur d’analyse, car une sous-routine a démarré, mais n’est pas terminée.  
  
 Pour plus d’informations sur les États de script, consultez la section États du moteur de script des [moteurs de script Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)