---
title: IDebugField::GetInfo - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b3251db3426f87901ca0768800feaa36fef5373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728844"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Cette méthode obtient des informations affichage sur le terrain.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
[dans] Une combinaison de [constantes FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) qui sélectionne les informations à afficher. Si le champ représente un symbole, c’est généralement le nom et le type de symbole.

`pFieldInfo`\
[out] Retourne l’information dans la structure [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) fournie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
