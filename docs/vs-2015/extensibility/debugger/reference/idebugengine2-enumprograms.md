---
title: IDebugEngine2::EnumPrograms | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::EnumPrograms
helpviewer_keywords:
- IDebugEngine2::EnumPrograms
ms.assetid: 56bf98eb-beec-4e5f-9ebe-46c922e54c56
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64a06b0791d76a0fbb9397bf1e3fe6ece4cdbaa7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907779"
---
# <a name="idebugengine2enumprograms"></a>IDebugEngine2::EnumPrograms
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère une liste de tous les programmes en cours de débogage par un moteur de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```csharp  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) objet qui contient une liste de tous les programmes en cours de débogage par un DE.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)

