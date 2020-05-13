---
title: IDebugCoreServer3::EnableAutoAttach ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732908"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permet l’attachement automatique pour les moteurs de débogé spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Paramètres
`rgguidSpecificEngines`\
[dans] Array de GUIDs pour chaque moteur de débogé à la marque comme auto-attachement.

`celtSpecificEngines`\
[dans] Le nombre de `rgguidSpecificEngines`moteurs spécifiés dans .

`pszStartPageUrl`\
[dans] L’URL de départ à utiliser lors de l’auto-fixation.

`pbstrSessionID`\
[out] ID de la session qui était auto-joint.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur. Un code `E_AUTO_ATTACH_NOT_REGISTERED`d’erreur est , ce qui indique que l’usine de classe de joint automatique n’a pas été enregistrée.

## <a name="remarks"></a>Notes
 Lorsqu’un programme associé à l’URL spécifiée est lancé, les moteurs de débogé spécifiés sont automatiquement démarrés et fixés.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
