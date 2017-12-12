---
title: JsContextRef, typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>JsContextRef, typedef
Une référence à un contexte de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Remarques  
 Chaque contexte de script contient son propre objet global, distinct de l'objet global des autres contextes de script.  
  
 De nombreuses API d'hébergement Chakra nécessitent un contexte de script « actif », qui peut être défini à l'aide de `JsSetCurrentContext`. Quand les API hébergeant Chakra nécessitent un contexte actif à définir, leur documentation l'indique explicitement.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)