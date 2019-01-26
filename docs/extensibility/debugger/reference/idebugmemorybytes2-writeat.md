---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92b0438820d776dce7eb9fd5bd7e1c049d449b14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035326"
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
 [in] Octets à écrire. Ce tableau est censé pour être au moins `dwCount` octets de taille.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si tous les octets peut être écrite ou retourne un code d’erreur (généralement `E_FAIL`).  
  
## <a name="remarks"></a>Notes  
 Si l’adresse de départ n’est pas dans la fenêtre mémoire représentée par ce [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) de l’objet, aucune écriture ne se produit et le code d’erreur `E_FAIL` est retourné, même si la quantité pour écrire des chevauchements dans l’espace de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)