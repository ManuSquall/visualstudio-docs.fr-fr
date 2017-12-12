---
title: JsNativeFunction, typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativefunction-typedef"></a>JsNativeFunction, typedef
Un rappel de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 appelé  
 Un objet `Function` qui représente la fonction appelée.  
  
 isConstructCall  
 Indique s'il s'agit d'un appel régulier ou d'un « nouvel » appel.  
  
 arguments  
 Les arguments pour l'appel.  
  
 argumentCount  
 Le nombre d'arguments.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Le résultat de l'appel, s'il y en a un.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)