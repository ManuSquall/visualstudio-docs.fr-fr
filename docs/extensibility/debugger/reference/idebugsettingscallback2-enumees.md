---
description: Énumère les évaluateurs d’expressions disponibles en fonction des identificateurs de langue et de fournisseur.
title: 'IDebugSettingsCallback2 :: enums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7606bd46587c7141bddea0c822f08459f2d262d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075664"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Énumère les évaluateurs d’expressions disponibles en fonction des identificateurs de langue et de fournisseur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Paramètres
`celtBuffer`\
dans Nombre d’éléments dans la `pceltEEs` mémoire tampon.

`rgguidLang`\
[in, out] Identificateur unique du langage de programmation.

`rgguidVendor`\
[in, out] Identificateur unique du fournisseur.

`pceltEEs`\
[in, out] Tableau d’évaluateurs d’expression.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
