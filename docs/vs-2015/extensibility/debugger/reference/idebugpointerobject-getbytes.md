---
title: IDebugPointerObject::GetBytes | Microsoft Docs
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
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce8537f493fb7b459f8ca9334634bd997a138037
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923119"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la valeur désignée comme une série d’octets consécutifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwStart`  
 [in] Offset, en octets, à partir du début de l’objet désigné.  
  
 `dwCount`  
 [in] Le nombre d’octets à récupérer.  
  
 `pBytes`  
 [in, out] Un tableau est rempli avec la valeur comme une série d’octets consécutifs, en commençant à l’offset donné à partir de l’objet désigné.  
  
 `pdwBytes`  
 [out] Retourne le nombre d’octets réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée si le pointeur comme représenté par ce [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) pointe vers un type primitif ou un simple tableau de types primitifs (autrement dit, un tableau qui peut être représenté par une simple séquence d’octets).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)

