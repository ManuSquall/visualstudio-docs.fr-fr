---
title: IDebugThread2::EnumFrameInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a906cb23432c9b51d80ee6e0ff97cc5d30f2a665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Récupère une liste des frames de pile pour ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Une combinaison d’indicateurs à partir de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) énumération qui spécifie les champs de la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures doivent être remplis. Spécifiez le `FIF_FUNCNAME_FORMAT` indicateur pour mettre en forme le nom de fonction dans une chaîne unique.  
  
 `nRadix`  
 [in] Base utilisée dans la mise en forme des informations numériques dans l’énumérateur.  
  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) objet qui contient une liste de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures décrivant le frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les cadres du thread sont énumérées dans l’ordre, avec le frame actuel énumérée en premier et le frame plus anciens énumérées en dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)