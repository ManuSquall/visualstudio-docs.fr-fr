---
title: IDebugPortPicker::DisplayPortPicker - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724891"
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
[dans] Poignée pour la boîte de dialogue parent.

`pbstrPortId`\
[out] Chaîne d’identification de port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Une valeur `S_FALSE` de retour de `S_OK` (ou `BSTR` une `NULL`valeur de retour de avec l’ensemble à ) indique que l’utilisateur a cliqué **Annuler**.

## <a name="see-also"></a>Voir aussi
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
