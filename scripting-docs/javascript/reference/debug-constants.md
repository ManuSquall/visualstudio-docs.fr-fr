---
title: Constantes de débogage | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636149"
---
# <a name="debug-constants"></a>Constantes de débogage
Les constantes Debug retournent des valeurs constantes qui sont des propriétés de l'objet `Debug`.  
  
## <a name="debug-object-constants"></a>Constantes de l'objet Debug  
 Le tableau suivant répertorie les valeurs constantes qui sont des propriétés de la [objet Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Constante|Description|Valeur|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|L’élément de travail synchrone a affecté un rappel ou une continuation, qui doit être exécuté par une opération asynchrone.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|L’élément de travail synchrone a satisfait une partie d’une opération asynchrone de jointure.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|L’élément de travail synchrone a satisfait une opération asynchrone choisie.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|L’élément de travail synchrone a été annulé.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|L’élément de travail synchrone a provoqué une erreur dans une opération asynchrone.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|L'opération d'annulation asynchrone a réussi.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|L'opération d'annulation asynchrone a été annulée.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|L'opération asynchrone a provoqué une erreur.|3|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Fonction Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)