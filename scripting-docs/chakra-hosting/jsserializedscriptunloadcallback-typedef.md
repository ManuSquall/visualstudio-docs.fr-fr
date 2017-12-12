---
title: JsSerializedScriptUnloadCallback, typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>JsSerializedScriptUnloadCallback, typedef
Appelé par le runtime quand il en a terminé avec toutes les ressources liées à l’exécution du script.     L’appelant doit libérer la source si elle est chargée, le code d’octet et le contexte à ce moment-là.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `sourceContext`  
 Contexte passé à `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Remarques  
  
> [!WARNING]
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)