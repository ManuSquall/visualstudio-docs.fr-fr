---
title: IDebugArrayObject2::HasBaseIndices | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9d0c06ad921ad43bcb7a79446062bc6feda8009
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423645"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Détermine si le tableau a des index de base (limites inférieures) défini.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>Paramètres
 `pfHasBaseIndices`\

 [out] TRUE pour spécifier que le tableau a des index de base (limites inférieures) ; Sinon, FALSE.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.