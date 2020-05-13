---
title: IDebugDocumentContext2::Compare Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731882"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compare ce contexte de document à un éventail donné de contextes documentaires.

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
[dans] Une valeur de [l’énumération DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) qui spécifie le type de comparaison.

`rgpDocContextSet`\
[dans] Un tableau d’objets [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui représentent les contextes de documents comparés à.

`dwDocContextSetLen`\
[dans] La longueur de la gamme de contextes de documents à comparer.

`pdwDocContext`\
[out] Retourne l’indice `rgpDocContextSet` dans la gamme du premier contexte de document qui satisfait la comparaison.

## <a name="return-value"></a>Valeur de retour
 Retourne `S_OK` si une correspondance a été trouvée. Retours `S_FALSE` si aucun match n’a été trouvé. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les objets [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) qui sont passés dans le tableau doivent être implémentés par le même moteur de débogé qui met en œuvre l’objet `IDebugDocumentContext2` appelé; autrement, la comparaison n’est pas valide.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
