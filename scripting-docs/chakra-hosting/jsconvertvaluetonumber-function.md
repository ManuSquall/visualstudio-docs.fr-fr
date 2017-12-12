---
title: JsConvertValueToNumber, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsConvertValueToNumber
helpviewer_keywords: JsConvertValueToNumber function
ms.assetid: c47b8653-0591-4863-b8b5-33187b315816
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db3ebb8b49f197232c5137bf42151491ebee35ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsconvertvaluetonumber-function"></a>JsConvertValueToNumber, fonction
Convertit la valeur en nombre à l'aide de la sémantique JavaScript standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToNumber(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *numberValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value`  
 Valeur à convertir.  
  
 `numberValue`  
 Valeur convertie.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)