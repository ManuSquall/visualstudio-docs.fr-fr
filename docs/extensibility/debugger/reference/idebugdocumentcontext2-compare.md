---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1416092661ee26bff773ea1a439c241a0f5c5fc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921513"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compare ce contexte de document dans un tableau des contextes de document donné.

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

#### <a name="parameters"></a>Paramètres
 `compare`

 [in] Une valeur comprise entre le [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) énumération qui spécifie le type de comparaison.

 `rgpDocContextSet`

 [in] Un tableau de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objets qui représentent les contextes de document en cours de comparaison.

 `dwDocContextSetLen`

 [in] La longueur du tableau de contextes de document à comparer.

 `pdwDocContext`

 [out] Retourne l’index dans le `rgpDocContextSet` tableau du premier contexte de document qui satisfait à la comparaison.

## <a name="return-value"></a>Valeur de retour
 Retourne `S_OK` si une correspondance a été trouvée. Retourne `S_FALSE` si aucune correspondance n’a été trouvée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objets qui sont passés dans le tableau doivent être implémentées par le même moteur de débogage qui implémente le `IDebugDocumentContext2` de l’objet qui est appelée ; sinon, la comparaison n’est pas valide.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)