---
description: Énumère les valeurs valides qui représentent les genres d’informations à effectuer à partir d’un objet IDebugField et s’affichent à l’utilisateur.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5632c6844a38f1891070311fe3c7c65a0220def5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151022"
---
# <a name="displaykind"></a>DisplayKind
Énumère les valeurs valides qui représentent les genres d’informations à effectuer à partir d’un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et s’affichent à l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Champs
`DisplayKind_Value`\
Valeur du champ.

`DisplayKind_Name`\
Nom du champ.

`DisplayKind_Type`\
Type de champ.

## <a name="requirements"></a>Configuration requise
En-tête : EE. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
