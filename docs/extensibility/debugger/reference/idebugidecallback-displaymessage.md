---
title: IDebugIDECallback::DisplayMessage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04727fc05de87181195aae2afb9dc20d627c256a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111698"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Envoie la chaîne du message spécifié à la fenêtre de sortie du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 [in] Chaîne du message à afficher dans la fenêtre de sortie du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)