---
title: JsCreateExternalArrayBuffer, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568029"
---
# <a name="jscreateexternalarraybuffer-function"></a>JsCreateExternalArrayBuffer (fonction)
Crée un objet `ArrayBuffer` Javascript pour accéder à la mémoire externe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `data`  
 Pointeur vers la mémoire externe.  
  
 `byteLength`  
 Nombre d’octets dans la mémoire externe.  
  
 `finalizeCallback`  
 Rappel au moment où l'objet est finalisé. Ce paramètre peut être null.  
  
 `callbackState`  
 État fourni par l’utilisateur qui sera repassé à finalizeCallback.  
  
 `result`  
 Nouvel objet `ArrayBuffer` .  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)