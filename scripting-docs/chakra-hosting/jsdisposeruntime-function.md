---
title: JsDisposeRuntime, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDisposeRuntime
helpviewer_keywords:
- JsDisposeRuntime function
ms.assetid: 0aefde3f-7250-48be-afc5-53ea85c12f30
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33b24b522e30edb748c93251d6e1962af3be5f60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567799"
---
# <a name="jsdisposeruntime-function"></a>JsDisposeRuntime, fonction
Supprime un runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsDisposeRuntime(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Runtime à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Une fois qu'un runtime a été supprimé, toutes les ressources détenues par celui-ci ne sont pas valides et ne peuvent pas être utilisées. Si le runtime est actif (autrement dit, s’il est défini pour être utilisé sur un thread particulier), il ne peut pas être supprimé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)