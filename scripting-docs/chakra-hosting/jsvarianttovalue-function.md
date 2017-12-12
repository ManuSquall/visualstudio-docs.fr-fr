---
title: JsVariantToValue, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsVariantToValue
helpviewer_keywords: JsVariantToValue function
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc778d87aab7e80e7c1b04a68c2d3b9c6fdd885a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsvarianttovalue-function"></a>JsVariantToValue, fonction
Crée une valeur JavaScript qui est une projection de l'élément `VARIANT` transféré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `variant`  
 `VARIANT` à projeter.  
  
 `value`  
 Valeur JavaScript qui est une projection de l'élément `VARIANT`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 La valeur projetée peut être utilisée par le script pour appeler un objet COM Automation à partir du script. Les hôtes sont chargés d'appliquer les règles de thread COM.  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)