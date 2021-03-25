---
description: Crée un ID unique pour cette propriété afin de s’assurer qu’elle est unique parmi toutes les autres propriétés.
title: 'IDebugProperty3 :: CreateObjectID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af90f360e59e04cc5d55017c5d986e6682bab2ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064811"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crée un ID unique pour cette propriété afin de s’assurer qu’elle est unique parmi toutes les autres propriétés.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée lorsque le gestionnaire de débogage de session souhaite s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés. Le moteur DE débogage (DE) prend en charge cette méthode, sauf si les propriétés qu’elle traite sont déjà identifiées de manière unique. Si le DE ne prend pas en charge cette méthode, il retourne `E_NOTIMPL` .

 Tout ID unique créé avec `CreateObjectID` est détruit lorsque la méthode [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) est appelée ; cela signale également la fin de la nécessité d’identifier cette propriété de manière unique.

> [!NOTE]
> Il n’existe aucune méthode pour récupérer cet ID unique, DE sorte que le peut faire tout ce qu’il souhaite pour des ID uniques lorsque la `CreateObjectID` méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
