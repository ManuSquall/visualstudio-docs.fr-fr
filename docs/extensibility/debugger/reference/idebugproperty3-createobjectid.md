---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf17196b4dae8642a81664dd339eaa78c2d2d8e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412749"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crée un ID unique pour cette propriété pour vous assurer qu’il est unique parmi toutes les autres propriétés.

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
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée lorsque le Gestionnaire de session de débogage veut s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés. Le moteur de débogage (dé) prend en charge cette méthode, sauf si les propriétés qu'avec il traite sont déjà identifiées. Si le DE ne prend pas en charge cette méthode, elle retourne `E_NOTIMPL`.

 Un ID unique créé avec `CreateObjectID` est détruit lorsque le [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) méthode est appelée ; cela signale également la fin de la nécessité d’identifiant de manière unique cette propriété.

> [!NOTE]
> Il n’existe aucune méthode pour récupérer cet ID unique, donc le DE faire quoi pour les ID uniques lors de la `CreateObjectID` méthode est appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)