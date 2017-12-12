---
title: JsRunSerializedScript, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRunSerializedScript
helpviewer_keywords: JsRunSerializedScript function
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b770edbcaa4e7dc36f295407627c10a8b574b88b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscript-function"></a>JsRunSerializedScript, fonction
Exécute un script sérialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `script`  
 Le code source du script sérialisé.  
  
 `buffer`  
 Le script sérialisé.  
  
 `sourceContext`  
 Un cookie qui identifie le script utilisable par des contextes de scripts débogables.  
  
 `sourceUrl`  
 L'emplacement d'où provenait le script.  
  
 `result`  
 Le résultat de l'exécution du script, s'il y en a un. Ce paramètre peut avoir la valeur Null.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Nécessite un contexte de script actif.  
  
 La mémoire tampon n'est pas conservée dans la mémoire par le moteur de script : votre code doit donc la maintenir active tant qu'elle peut être utilisée pour exécuter des scripts.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)