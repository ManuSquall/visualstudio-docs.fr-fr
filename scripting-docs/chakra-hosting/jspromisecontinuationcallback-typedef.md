---
title: JsPromiseContinuationCallback, typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568599"
---
# <a name="jspromisecontinuationcallback-typedef"></a>JsPromiseContinuationCallback (typedef)
Rappel de continuation de promesse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Remarques  
 L'hôte peut spécifier un rappel de continuation de promesse dans `JsSetPromiseContinuationCallback`. Si un script crée une tâche à exécuter ultérieurement, le rappel de continuation de promesse sera appelé avec la tâche. La tâche doit donc être placée dans une file d'attente FIFO, pour être exécutée à la fin de l'exécution du script actuel.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)