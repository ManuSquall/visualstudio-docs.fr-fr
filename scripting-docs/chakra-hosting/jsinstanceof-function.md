---
title: Jsinstanceof, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94399a62-b996-4fd2-82ce-1c26e7a4da08
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00b5018ae3d04e6bcb361b1c765df61e5855d553
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsinstanceof-function"></a>JsInstanceOf, fonction
Effectue le test d’opérateur "instanceof" JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
JsInstanceOf(   
  _In_ JsValueRef object,  
  _In_ JsValueRef constructor,  
  _Out_ bool *result  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet à tester.  
  
 `constructor`  
 Fonction constructeur à tester.  
  
 `result`  
 Indique si "object instanceof constructor" a la valeur true.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)