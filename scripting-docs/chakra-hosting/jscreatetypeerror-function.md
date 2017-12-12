---
title: JsCreateTypeError, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsCreateTypeError
helpviewer_keywords: JsCreateTypeError function
ms.assetid: 8ef7bb77-2c98-482a-bccb-1f0fe2b826f5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42404084d7f6f75e5cdec6b9e4bf06f29b8a2136
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatetypeerror-function"></a>JsCreateTypeError, fonction
Crée un objet d'erreur JavaScript TypeError  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateTypeError(  
   _In_ JsValueRef message,  
   _Out_ JsValueRef *error  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `message`  
 Message de l'objet d'erreur.  
  
 `error`  
 Nouvel objet d'erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)