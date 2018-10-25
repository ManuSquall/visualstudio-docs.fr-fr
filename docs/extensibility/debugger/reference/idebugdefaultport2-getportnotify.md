---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb21f020f6a470b9fded56939987f0a03333206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872733"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Cette méthode obtient un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface pour ce port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppPortNotify`  
 [out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Normalement, le `QueryInterface` méthode est appelée sur l’objet qui implémente le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface pour obtenir un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface. Toutefois, il existe des circonstances dans lesquelles l’interface souhaitée est implémentée sur un autre objet. Cette méthode masque ces circonstances et retourne le `IDebugPortNotify2` interface à partir de l’objet le plus approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)