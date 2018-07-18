---
title: JsFinalizeCallback, Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aa7a0269-b9d4-4717-97ac-8da7eb6ced15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6efb6873e1bfc6c8689c0ae7939bb11cc7b311bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567999"
---
# <a name="jsfinalizecallback-typedef"></a>JsFinalizeCallback, typedef
Un rappel de finaliseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void (CALLBACK *JsFinalizeCallback)(  
   _In_opt_ void *data  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Données  
 Les données externes qui ont été passées en entrée lors de la création de l'objet à finaliser.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)