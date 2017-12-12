---
title: JsSetException, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetException
helpviewer_keywords: JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexception-function"></a>JsSetException, fonction
Définit le runtime du contexte actuel dans un état d'exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `exception`  
 Exception JavaScript à définir pour le runtime du contexte actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 `JsNoError` si le moteur a été défini dans un état d'exception, sinon, un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Si le runtime du contexte actuel est déjà dans un état d'exception, cette API retourne `JsErrorInExceptionState`.  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)