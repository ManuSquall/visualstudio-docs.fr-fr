---
title: "DEBUG_TEXT, constantes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# DEBUG_TEXT, constantes
Utilisé pendant l'[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## Syntaxe  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## Constantes  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|VALEUR DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indique que le texte est une expression par opposition à une instruction.  Cet indicateur peut affecter la façon dont le texte est analysé par certains langages.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, elle sera utilisée par l'appelant.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|N'autorisez pas les effets secondaires.  Si cet indicateur est défini, l'évaluation ne doit modifier aucun état d'exécution.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Autorisez les points d'arrêt pendant l'évaluation du texte.  Si cet indicateur n'est pas défini, les points d'arrêt sont ignorés pendant l'évaluation du texte.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Autorisez les rapports d'erreurs pendant l'évaluation du texte.  Si cet indicateur n'est pas défini, les erreurs ne seront pas enregistrées dans l'hôte pendant l'évaluation.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indique que l'expression sera évaluée à un contexte de code au lieu d'exécuter l'expression elle\-même.|  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)