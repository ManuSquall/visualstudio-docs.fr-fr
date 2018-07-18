---
title: JsCreateDataView, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5150a9b858e09217ee7ac3c1f25efba36615f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567979"
---
# <a name="jscreatedataview-function"></a>JsCreateDataView (fonction)
Crée un objet `DataView` Javascript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayBuffer`  
 Objet `ArrayBuffer` existant à utiliser comme stockage pour l'objet résultat `DataView`.  
  
 `byteOffset`  
 Décalage en octets du début de l'objet `arrayBuffer` pour l'objet résultat `DataView` à la référence.  
  
 `byteLength`  
 Nombre d'octets dans l'objet ArrayBuffer pour l'objet résultat DataView à référencer.  
  
 `result`  
 Nouvel objet DataView.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)