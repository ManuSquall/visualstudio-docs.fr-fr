---
title: 'IDebugArrayField :: GetRank, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10f42ca10496d89955032bd531651186d0aecf37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926346"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le rang d’un tableau correspond au nombre de dimensions. En C++ et C#, les tableaux multidimensionnels sont vraiment des tableaux de tableaux et peuvent donc être considérés comme un tableau unidimensionnel (et la `GetRank` méthode retourne toujours 1). En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] revanche, les tableaux multidimensionnels sont gérés différemment et le rang d’un tel tableau reflète le nombre de dimensions (et la `GetRank` méthode retourne toujours le nombre de dimensions).

## <a name="see-also"></a>Voir aussi
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
