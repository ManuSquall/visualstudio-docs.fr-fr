---
description: Obtient des informations sur ce module.
title: 'IDebugModule2 :: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69286a7bf50c32aa3aa720deff78ee957f53fc65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065656"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Obtient des informations sur ce module.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
dans Combinaison d’indicateurs de l’énumération [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) qui spécifie les champs de `pInfo` à remplir.

`pInfo`\
[in, out] Structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) qui est remplie avec une description du module.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La structure [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contient le nom du module affiché dans la fenêtre **modules** .

## <a name="see-also"></a>Voir aussi
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
