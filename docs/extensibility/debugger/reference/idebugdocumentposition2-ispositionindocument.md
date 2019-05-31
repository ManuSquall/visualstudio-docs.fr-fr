---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab4792427a98f97fcd50d4b39c2bb332527a0942
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333410"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Détermine si la position du document se trouve dans le document donné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Paramètres
`pDoc`\
[in] Le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objet qui représente le candidat de document conteneur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée principalement dans la définition des points d’arrêt dans [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaces. Comme les documents sont chargés, la position du point d’arrêt est appelée pour déterminer si le document contient cette position.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)