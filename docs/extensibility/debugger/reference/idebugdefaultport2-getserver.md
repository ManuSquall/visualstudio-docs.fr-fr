---
title: IDebugDefaultPort2::GetServer | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::GetServer
helpviewer_keywords: IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1d5839db305c1395edc24a95de706cfc2072d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Cette méthode obtient une interface pour le serveur sur ce port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppServer`  
 [out] Retourne un objet qui implémente le [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) est implémentée par Visual Studio et représente le port se trouve sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)