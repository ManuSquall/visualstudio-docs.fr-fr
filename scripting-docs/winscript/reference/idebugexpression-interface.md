---
title: "IDebugExpression, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression (interface)"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression, interface
Représente une expression évaluée de façon asynchrone.  Les moteurs de script implémentent généralement cette interface.  Un débogueur IDE utilise généralement cette interface pour activer une fenêtre ou une fenêtre Espion immédiate d'exécution.  
  
> [!NOTE]
>  L'interface d' `IDebugExpression` est fourni uniquement à partir d'un frame de pile.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugExpression` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Démarre l'évaluation de l'expression.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Interrompt l'expression.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Détermine si l'opération est terminée.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Retourne le résultat de l'évaluation d'une expression sous forme de chaîne et valeur de retour de l'exécution.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Retourne le résultat de l'évaluation de l'expression comme propriété de débogage et valeur de retour de l'exécution.|