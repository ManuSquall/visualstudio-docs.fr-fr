---
title: IEnumDebugCodeContexts2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Clone
helpviewer_keywords:
- IEnumDebugCodeContexts2::Clone
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe7a3929726b5708884f96b624aac7b453f4c8d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331384"
---
# <a name="ienumdebugcodecontexts2clone"></a>IEnumDebugCodeContexts2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
[out] Retourne une copie de cette énumération en tant qu’objet distinct.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et la version d’origine sont distincts et peuvent être modifiées individuellement.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)