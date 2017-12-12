---
title: JsParseScript, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsParseScript
helpviewer_keywords: JsParseScript function
ms.assetid: e9d0e363-7cbe-43eb-9dc0-1f47e586c9ab
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de55c249b6fb5b723086f48312904f0232f0a11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsparsescript-function"></a>JsParseScript, fonction
Analyse un script et retourne une fonction représentant le script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsParseScript(  
   _In_z_ const wchar_t *script,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `script`  
 Le script à analyser.  
  
 `sourceContext`  
 Un cookie qui identifie le script utilisable par des contextes de scripts débogables.  
  
 `sourceUrl`  
 L'emplacement d'où provenait le script.  
  
 `result`  
 Une fonction représentant le code du script.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)