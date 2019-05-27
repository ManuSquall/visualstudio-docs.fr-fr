---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00923556927f2fed7e5895df2db391a45463e57e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212905"
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
[in] Handle de la boîte de dialogue parent.

`pbstrPortId`\
[out] Chaîne d’identificateur de port.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. La valeur de retour `S_FALSE` (ou une valeur de retour de `S_OK` avec la `BSTR` définie sur `NULL`) indique que l’utilisateur a cliqué **Annuler**.

## <a name="see-also"></a>Voir aussi
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)