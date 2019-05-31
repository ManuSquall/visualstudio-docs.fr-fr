---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c667ffa597481121de0467c9ab4b07e4bf4d607
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333385"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Récupère la plage pour la position actuelle du document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Paramètres
`pdwBegOffset`\
[in, out] Décalage de la position de début de la plage. Définissez ce paramètre sur une valeur null si cette information n’est pas nécessaire.

`pdwEndOffset`\
[in, out] Décalage de la position de fin de la plage. Définissez ce paramètre sur une valeur null si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La plage spécifiée dans une position de document pour un point d’arrêt de l’emplacement est utilisée par le moteur de débogage (dé) pour rechercher à l’avance pour une instruction qui apporte réellement le code. Considérons par exemple le code suivant :

```
Line 5: // comment
Line 6: x = 1;
```

 La ligne 5 ne contribue aucun code pour le programme en cours de débogage. Si le débogueur qui définit le point d’arrêt sur la ligne 5 veut le DE pour rechercher vers le bas une certaine quantité de la première ligne qui contribue le code, le débogueur spécifiez une plage qui comprend des lignes de candidat supplémentaire où un point d’arrêt peut être placé correctement. Le DE puis rechercherait vers l’avant via ces lignes jusqu'à ce qu’il trouve une ligne qui peut accepter un point d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)