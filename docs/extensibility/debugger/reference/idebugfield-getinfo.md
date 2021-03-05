---
description: Cette méthode obtient des informations affichables sur le champ.
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
ms.openlocfilehash: c681fef38377f0ce8e74b45dba065b5eae39462c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151933"
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
