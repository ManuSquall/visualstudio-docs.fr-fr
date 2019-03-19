---
title: Interface IDebugExpression | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 589c231afbc149c4eeface784d3cdbd43c4e5e40
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156344"
---
# <a name="idebugexpression-interface"></a>IDebugExpression, interface
Représente une expression évaluée de façon asynchrone. En général, les moteurs de script implémentent cette interface. En règle générale, un IDE de débogueur utilise cette interface pour activer une fenêtre de l’exécution immédiate ou de fenêtre Espion.  
  
> [!NOTE]
>  Le `IDebugExpression` interface est disponible uniquement à partir d’un frame de pile.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugExpression` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Commence l’évaluation de l’expression.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Abandonne l’expression.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Détermine si l’opération est terminée.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Retourne le résultat de l’évaluation de l’expression comme une chaîne et la valeur de retour de l’opération.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Retourne le résultat de l’évaluation des expressions en tant que propriété de débogage et de la valeur de retour de l’opération.|