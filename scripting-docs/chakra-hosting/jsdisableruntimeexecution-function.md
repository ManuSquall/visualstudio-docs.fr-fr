---
title: JsDisableRuntimeExecution, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568269"
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution, fonction
Suspend l'exécution du script et met fin à tous les scripts en cours dans un runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Runtime à suspendre.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Les appels à un runtime suspendu échouent tant que `JsEnableRuntimeExecution` n'est pas appelé.  
  
 Cette API n'a pas besoin d'être appelée sur le thread sur lequel le runtime est actif. Même si le runtime est défini dans un état suspendu, un script en cours d'exécution ne peut pas être suspendu immédiatement. Il doit être terminé par une exception non interceptable dès que possible.  
  
 La suspension de l'exécution dans un runtime déjà suspendu est une opération nulle.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)