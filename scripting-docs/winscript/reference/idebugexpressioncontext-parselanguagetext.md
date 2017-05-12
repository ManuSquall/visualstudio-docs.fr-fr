---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
Crée une expression de débogage pour le texte spécifié.  
  
## Syntaxe  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### Paramètres  
 `pstrCode`  
 \[in\]  fournit le texte de l'expression ou des instructions.  
  
 `nRadix`  
 \[in\]  Radis à utiliser.  
  
 `pstrDelimiter`  
 \[in\]  le séparateur d'END\-de\-script\-bloc.  Lorsque `pstrCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \('\), pour détecter la fin du bloc de script.  Ce paramètre spécifie que le séparateur qui l'hôte utilisé, ce qui permet au moteur de script pour fournir du prétraitement primitive conditionnel \(par exemple, en remplaçant un guillemet simple \[« \] par deux guillemets simples pour l " utilisation comme séparateur\).  Exactement comment \(et\) si le moteur de script utilise ces informations dépendent du moteur de script.  Affectez à ce paramètre la `NULL` si l'hôte n'avait pas l'habitude un séparateur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 \[in\]  La combinaison des opérations de débogage des balises de texte :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indique que le texte est une expression par opposition à une instruction.  Cette balise peut affecter la manière dont le texte est analysé par certains langages.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, elle sera utilisée par l'appelant.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|N'autorisez pas les effets secondaires.  Si cette balise est définie, l'évaluation de l'expression ne devez modifier aucun état d'exécution.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Autorise les points d'arrêt pendant l'évaluation du texte.  Si cet indicateur n'est pas définie ensuite des points d'arrêt sont ignorés pendant l'évaluation du texte.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Autorise les rapports d'erreurs pendant l'évaluation du texte.  Si cet indicateur n'est pas définie ensuite des erreurs ne sont pas stockées à l'hôte pendant l'évaluation.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indique l'expression doit être évaluée à un contexte de code au lieu d'exécuter l'expression elle\-même|  
  
 `ppe`  
 \[out\]  Retourne l'expression de débogage pour le texte spécifié.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode crée une expression de débogage pour le texte spécifié.  
  
## Voir aussi  
 [IDebugExpressionContext, interface](../../winscript/reference/idebugexpressioncontext-interface.md)