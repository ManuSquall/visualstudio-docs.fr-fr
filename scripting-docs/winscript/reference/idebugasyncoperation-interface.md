---
title: Interface IDebugAsyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821781"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation, interface
Le Gestionnaire de débogage de processus implémente le `IDebugAsyncOperation` interface. Un moteur de langage appelle le `IDebugApplication::CreateAsyncDebugOperation` méthode pour obtenir une référence à cette interface. Le moteur de langage peut utiliser le `IDebugAsyncOperation` interface pour fournir l’accès asynchrone à une opération de débogage synchrone.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugAsyncOperation` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Retourne l’opération de débogage synchrone associée à cet objet.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|L’opération asynchrone commencer.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annule une opération.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Détermine si l’opération de débogage est terminée.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fournit la valeur de retour et le paramètre d’objet de retour à partir de l’opération de débogage synchrone.|