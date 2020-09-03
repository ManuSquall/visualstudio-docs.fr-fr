---
title: 'IDebugDefaultPort2 :: GetPortNotify | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0f5b1faf000ef982e38736b3cd3ea89a1dc2dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196280"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient une interface [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) pour ce port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppPortNotify`  
 à Objet [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Normalement, la `QueryInterface` méthode est appelée sur l’objet implémentant l’interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) pour obtenir une interface [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Toutefois, dans certains cas, l’interface souhaitée est implémentée sur un objet différent. Cette méthode masque ces circonstances et retourne l' `IDebugPortNotify2` interface à partir de l’objet le plus approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
