---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 269a49a21fdf2c42c716fba1ab3c8cb293e15a1a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340035"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Cette méthode récupère un objet qui permet l’énumération de la liste des ports persistantes.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`PortNames`\
[in] Un [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) structure qui contient une liste de noms de ports pour trouver et retourner entre les ports persistantes. Seuls ports persistantes avec ces noms sont retournés.

`ppEnum`\
[out] Un objet qui implémente le [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interface.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Ports persistantes sont chargés lorsqu’un fournisseur de port est instancié et enregistré lorsque le fournisseur de port est détruit.

## <a name="see-also"></a>Voir aussi
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)