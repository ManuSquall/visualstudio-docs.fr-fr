---
description: Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur de sélectionner un port.
title: IDebugPortPicker ::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072310"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur de sélectionner un port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Paramètres
`hwndParentDialog`\
dans Handle de la boîte de dialogue parente.

`pbstrPortId`\
à Chaîne de l’identificateur de port.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Une valeur de retour `S_FALSE` (ou une valeur de retour de `S_OK` avec la valeur `BSTR` `NULL` ) indique que l’utilisateur a cliqué sur **Annuler**.

## <a name="see-also"></a>Voir aussi
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
