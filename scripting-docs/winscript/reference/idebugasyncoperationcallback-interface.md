---
title: Interface IDebugAsyncOperationCallBack | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperationCallBack interface
ms.assetid: ccbe12fe-2aac-4d9f-9e70-601003f1a34d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c09a8262f2be474ea51a4e36cff40414e1cd2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146264"
---
# <a name="idebugasyncoperationcallback-interface"></a>IDebugAsyncOperationCallBack, interface
Fournit des événements d’état liés à la progression d’une évaluation d’interface `IDebugAsyncOperation`.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugAsyncOperationCallBack` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugAsyncOperationCallBack::onComplete](../../winscript/reference/idebugasyncoperationcallback-oncomplete.md)|Signale qu’un résultat est disponible à partir d’une opération de débogage asynchrone.|