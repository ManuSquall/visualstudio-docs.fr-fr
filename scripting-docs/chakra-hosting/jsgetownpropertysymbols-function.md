---
title: JsGetOwnPropertySymbols, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 57c431e3-de0b-4ed0-b750-87a86448daff
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5528acf52e16aa7b8896f3a69cc23465e23cb2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568319"
---
# <a name="jsgetownpropertysymbols-function"></a>JsGetOwnPropertySymbols (fonction)
Obtient la liste de toutes les propriétés des symboles de l'objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetOwnPropertySymbols(  
   _In_ JsValueRef object,  
   _Out_ JsValueRef *propertySymbols  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet à partir duquel obtenir les symboles de propriété.  
  
 `propertySymbols`  
 Tableau de symboles de propriété.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 Cette API est prise en charge uniquement en mode Edge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)