---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0964c94334ca0815b4410f6858dca5502b2f8a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678460"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Définit le fournisseur de services.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

#### <a name="parameters"></a>Paramètres
 `pSP`

 [in] Référence à l’interface du fournisseur de services.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée avant que toutes les autres méthodes sont appelées.

## <a name="see-also"></a>Voir aussi
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)