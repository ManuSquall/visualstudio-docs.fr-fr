---
title: IDebugDocumentPositionOffset2::GetRange ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731628"
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
[dans, dehors] Décalage pour la position de départ de la plage. Définissez ce paramètre à une valeur nulle si ces informations ne sont pas nécessaires.

`pdwEndOffset`\
[dans, dehors] Décalage pour la position de fin de la plage. Définissez ce paramètre à une valeur nulle si ces informations ne sont pas nécessaires.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La plage spécifiée dans une position de document pour un point de rupture de localisation est utilisée par le moteur de débogé (DE) pour rechercher à l’avance une déclaration qui contribue réellement au code. Considérons par exemple le code suivant :

```
Line 5: // comment
Line 6: x = 1;
```

 La ligne 5 ne fournit aucun code au programme en cours de déboisation. Si le débbuggeur qui définit le point d’arrêt sur la ligne 5 veut que le DE recherche un certain montant pour la première ligne qui contribue au code, le débogénaire spécifie une plage qui comprend des lignes de candidats supplémentaires où un point d’arrêt peut être correctement placé. Le DE chercherait alors vers l’avant à travers ces lignes jusqu’à ce qu’il trouve une ligne qui pourrait accepter un point d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
