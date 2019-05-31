---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8af316c9669b00ae8316888c6a7072d4737dd23d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352662"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Cette méthode compare ce champ avec le champ spécifié pour l’égalité.

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
[in] Champ à comparer à celui-ci.

## <a name="return-value"></a>Valeur de retour
 Si les champs sont identiques, retourne `S_OK`. Si les champs sont différents, retourne `S_FALSE.` sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)