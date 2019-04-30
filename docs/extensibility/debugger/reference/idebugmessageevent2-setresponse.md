---
title: IDebugMessageEvent2::SetResponse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b54c84c5f5c13424354c65201d290fbef83e055
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873161"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Définit la réponse, le cas échéant, à partir de la boîte de message.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetResponse( 
   DWORD dwResponse
);
```

```csharp
int SetResponse( 
   uint dwResponse
);
```

#### <a name="parameters"></a>Paramètres
 `dwResponse`

 [in] Spécifie la réponse, en utilisant les conventions de Win32 `MessageBox` (fonction). Consultez le [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) (fonction) pour plus d’informations.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)