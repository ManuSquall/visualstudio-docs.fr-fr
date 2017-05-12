---
title: "IDebugAsyncOperation, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation (interface)"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation, interface
Process Debug Manager implémente l'interface d' `IDebugAsyncOperation` .  Un moteur de langage appelle la méthode d' `IDebugApplication::CreateAsyncDebugOperation` pour obtenir une référence à cette interface.  Le moteur de langage peut utiliser l'interface d' `IDebugAsyncOperation` pour fournir l'accès à une opération asynchrone de débogage synchrone.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugAsyncOperation` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Retourne l'opération de débogage synchrone associé à cet objet.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Pour démarrer l'opération asynchrone.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annule une opération.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Détermine si l'opération de débogage est terminée.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fournit la valeur de retour et le paramètre d'objet de retour de l'opération de débogage synchrone.|