---
title: JsSetRuntimeMemoryLimit, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit, fonction
Définit la limite de mémoire actuelle pour un runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtime`  
 Runtime dont la limite de mémoire doit être définie.  
  
 `memoryLimit`  
 Nouvelle limite de mémoire du runtime, en octets, ou -1 pour aucune limite de mémoire.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Une limite de mémoire entraîne l'échec de toute opération qui dépasse la limite avec une erreur « mémoire insuffisante ». La définition de la limite de mémoire d'un runtime avec la valeur -1 signifie que le runtime n'a aucune limite de mémoire. Par défaut, les nouveaux runtimes n'ont pas de limite de mémoire. Si la nouvelle limite de mémoire dépasse l'utilisation actuelle, l'appel réussi et toutes les futures allocations dans ce runtime échouent tant que l'utilisation de la mémoire du runtime ne descend pas en dessous de la limite.  
  
 La limite de mémoire d'un runtime peut toujours être définie, que le runtime soit actif ou non sur un autre thread.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)