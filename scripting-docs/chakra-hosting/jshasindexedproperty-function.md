---
title: JsHasIndexedProperty, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsHasIndexedProperty
helpviewer_keywords:
- JsHasIndexedProperty function
ms.assetid: 30436a3d-fda0-407e-aba2-142be2310372
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 786be053ee501f60c633cd4b93f7b73acaa9b68d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jshasindexedproperty-function"></a>JsHasIndexedProperty, fonction
Teste si un objet a une valeur au niveau de l'index spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsHasIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet à utiliser.  
  
 `index`  
 Index à tester.  
  
 `result`  
 Indique si l'objet a une valeur au niveau de l'index spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)