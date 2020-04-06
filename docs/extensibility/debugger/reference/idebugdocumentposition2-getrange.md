---
title: IDebugDocumentPosition2::GetRange ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731665"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtient la plage pour cette position de document.

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
[dans, dehors] Une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec le poste de départ. Définissez cet argument à une valeur nulle si cette information n’est pas nécessaire.

`pEndPosition`\
[dans, dehors] Une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de fin. Définissez cet argument à une valeur nulle si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La plage spécifiée dans une position de document pour un point de rupture de localisation est utilisée par le moteur de débogé (DE) pour rechercher à l’avance une déclaration qui contribue réellement au code. Considérons par exemple le code suivant :

```
Line 5: // comment
Line 6: x = 1;
```

 La ligne 5 ne fournit aucun code au programme en cours de déboisation. Si le débbuggeur qui définit le point d’arrêt sur la ligne 5 veut que le DE recherche un certain montant pour la première ligne qui contribue au code, le débogénaire spécifie une plage qui comprend des lignes de candidats supplémentaires où un point d’arrêt pourrait être correctement placé. Le DE chercherait alors vers l’avant à travers ces lignes jusqu’à ce qu’il trouve une ligne qui pourrait accepter un point d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
