---
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a114eee347382b5a351f86cee350dacf958626a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860047"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Cette méthode obtient l’état actuel de modifier & Continuer du processus. Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pReason`  
 [out] Une valeur comprise entre le [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
> [!NOTE]
>  Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
 Cet état peut être affecté par [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)