---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed978355aa752730cfb43390b3e4b6f80d327f83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919466"
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

#### <a name="parameters"></a>Paramètres
 `pField`

 [in] Champ à comparer à celui-ci.

## <a name="return-value"></a>Valeur de retour
 Si les champs sont identiques, retourne `S_OK`. Si les champs sont différents, retourne `S_FALSE.` sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)