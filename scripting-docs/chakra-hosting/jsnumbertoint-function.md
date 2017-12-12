---
title: JsNumberToInt, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsnumbertoint-function"></a>JsNumberToInt (fonction)
Récupère la valeur `int` d'une valeur numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value`  
 Valeur numérique à convertir en valeur `int`.  
  
 `intValue`  
 Valeur de l'objet `int`.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Cette fonction récupère la valeur d'une valeur numérique et la convertit en valeur `int`. Elle échoue avec `JsErrorInvalidArgument` si le type de la valeur n'est pas numérique.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)