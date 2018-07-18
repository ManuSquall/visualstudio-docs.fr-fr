---
title: IDebugMemoryBytes2::ReadAt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612a065286723e3c2b68a9ce5bd31c850d030959
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114084"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lit une séquence d’octets, en commençant à un emplacement donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStartContext`  
 [in] Le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet qui spécifie où commencer la lecture des octets.  
  
 `dwCount`  
 [in] Le nombre d’octets à lire. Indique également la longueur de la `rgbMemory` tableau.  
  
 `rgbMemory`  
 [dans, out] Tableau remplie avec les octets lus réellement.  
  
 `pdwRead`  
 [out] Retourne le nombre d’octets contigus réellement lus.  
  
 `pdwUnreadable`  
 [dans, out] Retourne le nombre d’octets illisibles. Peut-être une valeur null si le client ne souhaite pas le nombre d’octets illisibles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si 100 octets sont demandés et les 50 premières sont lisibles, les 20 suivant sont illisibles, et le 30 restants sont lisibles, cette méthode retourne :  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 Dans ce cas, étant donné que `*pdwRead + *pdwUnreadable < dwCount`, l’appelant doit effectuer un appel supplémentaire à lire les octets restants 30 des 100 d’origine demandée et le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet passé dans le `pStartContext` paramètre doit être avancé à 70.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)