---
title: JsIsRuntimeExecutionDisabled, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIsRuntimeExecutionDisabled
helpviewer_keywords:
- JsIsRuntimeExecutionDisabled function
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4827205a33d337445faf9b0e9812133f0de3e97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsisruntimeexecutiondisabled-function"></a>JsIsRuntimeExecutionDisabled, fonction
Retourne une valeur qui indique si l'exécution du script est désactivée dans le runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(    _In_ JsRuntimeHandle runtime,    _Out_ bool *isDisabled);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Spécifie le runtime pour lequel vérifier que l'exécution est désactivée.  
  
 `isDisabled`  
 `true` si l'exécution est désactivée ; sinon, `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)