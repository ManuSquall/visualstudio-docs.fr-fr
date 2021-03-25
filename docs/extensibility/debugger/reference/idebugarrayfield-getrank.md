---
description: Obtient le rang ou le nombre de dimensions du tableau.
title: 'IDebugArrayField :: GetRank, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058974"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtient le rang ou le nombre de dimensions du tableau.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Paramètres
`pdwRank`\
à Retourne le rang.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le rang d’un tableau correspond au nombre de dimensions. En C++ et C#, les tableaux multidimensionnels sont vraiment des tableaux de tableaux et peuvent donc être considérés comme un tableau unidimensionnel (et la `GetRank` méthode retourne toujours 1). En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] revanche, les tableaux multidimensionnels sont gérés différemment et le rang d’un tel tableau reflète le nombre de dimensions (et la `GetRank` méthode retourne toujours le nombre de dimensions).

## <a name="see-also"></a>Voir aussi
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
