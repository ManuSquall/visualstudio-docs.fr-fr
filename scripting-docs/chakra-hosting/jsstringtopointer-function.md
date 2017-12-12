---
title: JsStringToPointer, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStringToPointer
helpviewer_keywords: JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsstringtopointer-function"></a>JsStringToPointer, fonction
Récupère le pointeur de chaîne d'une valeur de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value`  
 Valeur de chaîne à convertir en pointeur de chaîne.  
  
 `stringValue`  
 Pointeur de chaîne.  
  
 `stringLength`  
 Longueur de la chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction récupère le pointeur de chaîne d'une valeur de chaîne. Elle échoue avec `JsErrorInvalidArgument` si le type de la valeur n'est pas une chaîne. La durée de vie de la chaîne retournée est identique à celle de la valeur dont elle provient, toutefois, le pointeur de chaîne n'est pas considéré comme une référence à la valeur (et donc ne l'empêchera pas d'être collectée).  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)