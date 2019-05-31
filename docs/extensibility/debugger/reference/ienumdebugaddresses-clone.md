---
title: IEnumDebugAddresses::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5de8bd89d928bafe86bec0a502c1a5427db2d5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330056"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Cette méthode retourne une copie de l’énumération actuelle comme un objet distinct.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugAddresses** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugAddresses ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
[out] Retourne une copie de cette énumération en tant qu’objet distinct.

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et la version d’origine sont distincts et peuvent être modifiées individuellement.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)