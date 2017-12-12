---
title: JsConvertValueToString, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsConvertValueToString
helpviewer_keywords: JsConvertValueToString function
ms.assetid: a97aca04-b2ce-446a-acf4-49cd6777a85c
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f670e4e3eafd675783dd3a5836ad6c7bb31cd786
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsconvertvaluetostring-function"></a>JsConvertValueToString, fonction
Convertit la valeur en chaîne à l'aide de la sémantique JavaScript standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToString(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *stringValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value`  
 Valeur à convertir.  
  
 `stringValue`  
 Valeur convertie.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)