---
description: Compare ce contexte de document à un tableau de contextes de document donné.
title: 'IDebugDocumentContext2 :: compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a680da6f33d3da37995eb26071c0ea5f1ddc2283
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066709"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compare ce contexte de document à un tableau de contextes de document donné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Paramètres
`compare`\
dans Valeur de l’énumération [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) qui spécifie le type de comparaison.

`rgpDocContextSet`\
dans Tableau d’objets [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représentent les contextes de document comparés à.

`dwDocContextSetLen`\
dans Longueur du tableau de contextes de document à comparer.

`pdwDocContext`\
à Retourne l’index dans le `rgpDocContextSet` tableau du premier contexte de document qui satisfait à la comparaison.

## <a name="return-value"></a>Valeur renvoyée
 Retourne `S_OK` si une correspondance a été trouvée. Retourne `S_FALSE` si aucune correspondance n’a été trouvée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les objets [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passés dans le tableau doivent être implémentés par le moteur de débogage qui implémente l' `IDebugDocumentContext2` objet appelé sur ; sinon, la comparaison n’est pas valide.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
