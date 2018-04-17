---
title: IDebugMemoryBytes2::WriteAt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d1d79d88baf9688fe68ff44d59dcd4d19baf9f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Écrit le nombre spécifié d’octets de mémoire, en commençant à l’adresse spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStartContext`  
 [in] Le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objet qui spécifie l’emplacement où commencer l’écriture d’octets.  
  
 `dwCount`  
 [in] Le nombre d’octets à écrire.  
  
 `rgbMemory`  
 [in] Octets à écrire. Ce tableau est censé pour être au moins `dwCount` taille en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si tous les octets peut être écrite ou retourne un code d’erreur (généralement `E_FAIL`).  
  
## <a name="remarks"></a>Notes  
 Si l’adresse de départ n’est pas dans la fenêtre de la mémoire représentée par ce [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) de l’objet, aucune écriture ne se produit et le code d’erreur `E_FAIL` est retournée, même si la quantité d’écrire chevauche l’espace mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)