---
title: JsConstructObject, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsConstructObject
helpviewer_keywords: JsConstructObject function
ms.assetid: b07d2440-db55-4a6a-8376-56b40a8039a1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 505136aacebc8ae2c643842c3ff180feed66e3e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsconstructobject-function"></a>JsConstructObject, fonction
Appelle une fonction en tant que constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsConstructObject(  
   _In_ JsValueRef function,  
   _In_reads_(argumentCount) JsValueRef *arguments,  
   _In_ unsigned short argumentCount,  
   _Out_opt_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `function`  
 Fonction à appeler en tant que constructeur.  
  
 `arguments`  
 Les arguments pour l’appel.  
  
 `argumentCount`  
 Nombre d’arguments passés à la fonction.  
  
 `result`  
 Valeur retournée par l'appel de la fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)