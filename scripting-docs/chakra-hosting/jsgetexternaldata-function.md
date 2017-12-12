---
title: JsGetExternalData, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetExternalData
helpviewer_keywords: JsGetExternalData function
ms.assetid: 1919e1da-3ea7-4269-a5fb-a3be06bd029b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da78672f85159070949d067867699cfb5223b31c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetexternaldata-function"></a>JsGetExternalData, fonction
Récupère les données d'un objet externe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsGetExternalData(  
   _In_ JsValueRef object,  
   _Out_ void **externalData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Objet externe.  
  
 `externalData`  
 Données externes stockées dans l'objet. Peut avoir la valeur null si aucune donnée externe n'est stockée dans l'objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)