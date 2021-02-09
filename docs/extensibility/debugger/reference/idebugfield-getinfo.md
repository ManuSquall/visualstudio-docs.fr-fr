---
title: 'IDebugField :: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21d80f222bdea8a8e17a9b74eefb7885cab0c289
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869906"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Cette méthode obtient des informations affichables sur le champ.

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
dans Combinaison de [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) constantes qui sélectionne les informations à afficher. Si le champ représente un symbole, il s’agit généralement du nom et du type de symbole.

`pFieldInfo`\
à Retourne les informations contenues dans la structure [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) fournie.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
