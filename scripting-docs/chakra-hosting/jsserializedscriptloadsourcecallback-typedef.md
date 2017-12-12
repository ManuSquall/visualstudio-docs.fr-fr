---
title: Jsserializedscriptloadsourcecallback, typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback, Typedef
Appelé par le runtime pour charger le code source du script sérialisé.     L’appelant doit conserver la mémoire tampon du script valide jusqu’à `JsSerializedScriptUnloadCallback`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `sourceContext`  
 Contexte passé à `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Script retourné.  
  
## <a name="remarks"></a>Remarques  
  
> [!WARNING]
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)