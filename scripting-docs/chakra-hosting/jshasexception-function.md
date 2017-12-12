---
title: JsHasException, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsHasException
helpviewer_keywords: JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>JsHasException, fonction
Détermine si le runtime du contexte actuel est dans un état d'exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hasException`  
 Indique si le runtime du contexte actuel est dans l'état d'exception.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Si un appel dans les résultats du runtime d'une exception (comme le résultat de l'exécution d'un script ou en raison d'un événement tel qu'un échec de conversion), le runtime est placé dans un « état d'exception ». Tous les appels dans n'importe quel contexte créé par le runtime (à l'exception des API d'exception) échouent avec `JsErrorInExceptionState` tant que l'exception n'est pas désactivée.  
  
 Si le runtime du contexte actuel est dans l'état d'exception quand un rappel retourne dans le moteur, ce dernier relève automatiquement l'exception.  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)