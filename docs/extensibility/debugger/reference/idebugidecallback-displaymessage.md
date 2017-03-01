---
title: IDebugIDECallback::DisplayMessage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3aa786eb2440112713883ed6c600fc845975127
ms.lasthandoff: 02/22/2017

---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Envoie la chaîne du message spécifié à la fenêtre de sortie du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```c#  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 [in] Chaîne de message à afficher dans la fenêtre de sortie du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
