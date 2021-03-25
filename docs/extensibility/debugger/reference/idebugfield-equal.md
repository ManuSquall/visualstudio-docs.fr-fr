---
description: Cette méthode compare l’égalité de ce champ avec le champ spécifié.
title: 'IDebugField :: EQUAL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58673703fa0e585095c9a82fe2c7a4bc3e14827c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077107"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Cette méthode compare l’égalité de ce champ avec le champ spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Paramètres
`pField`\
dans Champ à comparer à celui-ci.

## <a name="return-value"></a>Valeur renvoyée
 Si les champs sont identiques, retourne `S_OK` . Si les champs sont différents, retourne la valeur dans le `S_FALSE.` cas contraire, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
