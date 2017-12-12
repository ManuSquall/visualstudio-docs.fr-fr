---
title: JsValueToVariant, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsValueToVariant
helpviewer_keywords: JsValueToVariant function
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2beb0a72a8e19d38d80ab8bf29ce0478ba7f481f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetovariant-function"></a>JsValueToVariant, fonction
Initialise l'élément `VARIANT` transféré en tant que projection d'une valeur JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Valeur JavaScript à projeter en tant que `VARIANT`.  
  
 `variant`  
 Pointeur vers un struct `VARIANT` qui sera initialisé en tant que projection.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 L'élément `VARIANT` de projection peut être utilisé par les clients COM Automation pour appeler l'objet JavaScript projeté.  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)