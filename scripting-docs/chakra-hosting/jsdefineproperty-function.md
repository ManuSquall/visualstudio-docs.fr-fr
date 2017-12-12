---
title: JsDefineProperty, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsDefineProperty
helpviewer_keywords: JsDefineProperty function
ms.assetid: b2cf48d6-eb40-457c-aa8b-b16a50dc5d6a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f929dd875b2ba8bf95db8d5970a770ce2859484
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsdefineproperty-function"></a>JsDefineProperty, fonction
Définit la propriété d'un nouvel objet à partir d'un descripteur de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsDefineProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef propertyDescriptor,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet qui possède la propriété.  
  
 `propertyId`  
 ID de la propriété.  
  
 `propertyDescriptor`  
 Descripteur de propriété.  
  
 `result`  
 Indique si la propriété a été définie.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)