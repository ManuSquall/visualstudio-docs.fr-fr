---
title: IDebugObject2::CreateAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226d584a2773a342b8247ff337e686be2da6bf9b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690641"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Crée un identificateur unique ou un alias pour cet objet, ou retourne un alias existant.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

#### <a name="parameters"></a>Paramètres
 `ppAlias`

 [out] L’alias de nouveau (ou existant).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un alias est une étiquette qui représente un objet particulier, tandis que l’objet est en mémoire.

## <a name="see-also"></a>Voir aussi
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)