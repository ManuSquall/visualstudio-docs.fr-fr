---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "Énumération de EVALFLAGS"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie des indicateurs qui évaluation de l'expression de contrôle.  
  
## Syntaxe  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## Membres  
 EVAL\_RETURNVALUE  
 Spécifie que la valeur de retour, le cas échéant, est évaluée.  
  
 EVAL\_NOSIDEEFFECTS  
 Spécifie que les effets secondaires pour ne pas être autorisé.  
  
 EVAL\_ALLOWBPS  
 Spécifie arrêter sur les points d'arrêt.  
  
 EVAL\_ALLOWERRORREPORT  
 Spécifie le rapport d'erreurs à l'hôte pour activer.  Utilisée pour l'évaluation d'une expression dans le script dans Internet Explorer.  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 Les forces fonctionne pour être évaluées comme adresses, au lieu d'appeler la fonction.  
  
 EVAL\_NOFUNCEVAL  
 Empêché la fonction d'être évalué.  par exemple, considérez le jeton d' `int` dans l'expression `myExpression(int) + 10`.  cette fonction peut être correctement évaluée comme adresse, mais pas comme valeur.  
  
 EVAL\_NOEVENTS  
 Indicateur pour signaler que des événements qui se produisent pendant l'évaluation d'une expression ne doivent pas être transmis au gestionnaire de débogage de \(SDM\) session ou à l'IDE.  
  
## Notes  
 Ces indicateurs sont passées comme arguments aux méthodes d' [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) et d' [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .  
  
 Ces indicateurs peuvent être combinées avec une opération de bits OR.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)