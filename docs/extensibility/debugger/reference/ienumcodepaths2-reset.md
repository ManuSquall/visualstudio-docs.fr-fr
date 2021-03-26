---
description: Réinitialise l’énumération des chemins de code au premier élément.
title: 'IEnumCodePaths2 :: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac7be476f1ec119d43b8794e5d2e1be02d66f521
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091784"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Réinitialise l'énumération au premier élément.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une fois cette méthode appelée, le prochain appel à la méthode [suivante](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
