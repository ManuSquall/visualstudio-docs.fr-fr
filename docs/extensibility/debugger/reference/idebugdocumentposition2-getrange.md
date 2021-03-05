---
description: Obtient la plage de la position de ce document.
title: 'IDebugDocumentPosition2 :: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e886891c0d971bdad0916d5b243993e46a7ba57
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162717"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtient la plage de la position de ce document.

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
[in, out] Structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de départ. Définissez cet argument sur une valeur null si cette information n’est pas nécessaire.

`pEndPosition`\
[in, out] Structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est remplie avec la position de fin. Définissez cet argument sur une valeur null si cette information n’est pas nécessaire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La plage spécifiée dans une position de document pour un point d’arrêt d’emplacement est utilisée par le moteur de débogage (DE) pour rechercher une instruction qui contribue en fait au code. Considérons par exemple le code suivant :

```
Line 5: // comment
Line 6: x = 1;
```

 La ligne 5 n’apporte aucun code au programme en cours de débogage. Si le débogueur qui définit le point d’arrêt à la ligne 5 souhaite que le DE recherche transfère un certain montant pour la première ligne qui contribue au code, le débogueur spécifie une plage qui comprend des lignes de candidats supplémentaires où un point d’arrêt peut être placé correctement. La fonction DE recherche ensuite dans ces lignes jusqu’à ce qu’elle ait trouvé une ligne pouvant accepter un point d’arrêt.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
