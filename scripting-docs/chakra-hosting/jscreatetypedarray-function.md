---
title: JsCreateTypedArray, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatetypedarray-function"></a>JsCreateTypedArray (fonction)
Crée un objet tableau typé JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayType`  
 Type du tableau à créer.  
  
 `baseArray`  
 Tableau de base du nouveau tableau. Utilisez `JS_INVALID_REFERENCE` s'il n'y a pas de tableau de base.  
  
 `byteOffset`  
 Décalage, en octets, à partir du début de `baseArray` (`ArrayBuffer`) pour le tableau typé résultant à référencer. S'applique uniquement quand `baseArray` est un objet `ArrayBuffer`. Sinon, doit avoir la valeur 0.  
  
 `elementLength`  
 Nombre d’éléments dans le tableau. S'applique uniquement pour la création d'un tableau typé sans `baseArray` (où `baseArray` est `JS_INVALID_REFERENCE`) ou quand `baseArray` est un objet `ArrayBuffer`. Sinon, doit avoir la valeur 0.  
  
 `result`  
 Nouvel objet tableau typé.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 `baseArray` peut être un objet `ArrayBuffer`, un autre tableau typé ou un objet `Array` JavaScript. Le tableau typé retourné utilise `baseArray` s'il s'agit d'un objet `ArrayBuffer`. Sinon, une copie du tableau source sous-jacent est créée et utilisée.  
  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)