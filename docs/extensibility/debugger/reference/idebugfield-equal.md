---
title: IDebugField::Egalité Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729014"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Cette méthode compare ce domaine avec le champ spécifié pour l’égalité.

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
[dans] Le champ à comparer à celui-ci.

## <a name="return-value"></a>Valeur de retour
 Si les champs sont `S_OK`les mêmes, les retours . Si les champs sont `S_FALSE.` différents, retourne Sinon, renvoie un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
