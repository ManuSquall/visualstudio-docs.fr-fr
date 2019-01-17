---
title: Interface IDebugAsyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c0088fddd2661d6711c9a18495f4b8704f782b3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349987"
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