---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c67828e2d9e1cb0c75d272b57e7c6b610a84fdd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326468"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtient la plage de cette position du document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Paramètres
`pBegPosition`\
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de départ. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

`pEndPosition`\
[in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure est remplie avec la position de fin. Définissez cet argument à une valeur null si cette information n’est pas nécessaire.

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
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)