---
title: Jsbackgroundworkitemcallback, Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsbackgroundworkitemcallback-typedef"></a>JsBackgroundWorkItemCallback, typedef
Un rappel d’élément de travail d’arrière-plan.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 donnéesRappel  
 Argument de données passé au service de thread.  
  
## <a name="remarks"></a>Remarques  
 Il est passé au service de thread de l’hôte (s’il est spécifié) pour permettre à l’hôte d’appeler le rappel d’élément de travail sur le thread d’arrière-plan de son choix.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)