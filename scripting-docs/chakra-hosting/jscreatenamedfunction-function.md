---
title: JsCreateNamedFunction, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a55f3df1d086394a7431b355f037b33e3f4a86c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567719"
---
# <a name="jscreatenamedfunction-function"></a>JsCreateNamedFunction (fonction)
Crée une fonction JavaScript avec un nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 Nom de cette fonction qui sera utilisé dans les opérations de diagnostic et de transformation en chaîne.  
  
 `nativeFunction`  
 Méthode à appeler quand la fonction est appelée.  
  
 `callbackState`  
 État fourni par l'utilisateur qui sera repassé au rappel.  
  
 `function`  
 Nouvel objet de fonction.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)