---
title: IDebugExpression (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>IDebugExpression, interface
Représente une expression évaluée de façon asynchrone. En général, les moteurs de script implémentent cette interface. En règle générale, un débogueur IDE utilise cette interface pour activer une fenêtre de l’exécution immédiate ou de fenêtre Espion.  
  
> [!NOTE]
>  Le `IDebugExpression` interface est disponible uniquement à partir d’un frame de pile.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugExpression` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Commence l’évaluation de l’expression.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Abandonne l’expression.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Détermine si l’opération est terminée.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Retourne le résultat de l’évaluation d’une expression comme une chaîne et la valeur de retour de l’opération.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Retourne le résultat de l’évaluation des expressions en tant que propriété de débogage et de la valeur de retour de l’opération.|