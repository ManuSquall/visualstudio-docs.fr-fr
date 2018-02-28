---
title: IDebugAsyncOperation (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation, interface
Le Gestionnaire de déboguer des processus implémente la `IDebugAsyncOperation` interface. Un moteur de langage appelle la `IDebugApplication::CreateAsyncDebugOperation` méthode pour obtenir une référence à cette interface. Le moteur de langage peut utiliser le `IDebugAsyncOperation` interface pour fournir l’accès asynchrone à une opération synchrone de débogage.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugAsyncOperation` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Retourne l’opération de débogage synchrone associée à cet objet.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|L’opération asynchrone commencer.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annule une opération.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Détermine si l’opération de débogage terminée.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fournit la valeur de retour et le paramètre d’objet de retour à partir de l’opération de débogage synchrone.|