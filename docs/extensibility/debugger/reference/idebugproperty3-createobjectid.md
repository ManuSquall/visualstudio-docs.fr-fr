---
title: IDebugProperty3::CreateObjectID ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721177"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crée une pièce d’identité unique pour cette propriété pour s’assurer qu’elle est unique parmi toutes les autres propriétés.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée lorsque le gestionnaire de déboiffé session veut s’assurer que cette propriété est identifiée de façon unique parmi toutes les autres propriétés. Le moteur de débogé (DE) prend en charge cette méthode à moins que les propriétés qu’il traite sont déjà identifiées de manière unique. Si le DE ne prend pas `E_NOTIMPL`en charge cette méthode, il revient .

 Toute pièce d’identité unique créée avec `CreateObjectID` est détruite lorsque la méthode [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) est appelée; cela indique également la fin de la nécessité d’identifier uniquement cette propriété.

> [!NOTE]
> Il n’existe aucune méthode pour récupérer cette pièce d’identité unique, `CreateObjectID` de sorte que le DE peut faire ce qu’il veut pour les pièces d’identité uniques lorsque la méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
