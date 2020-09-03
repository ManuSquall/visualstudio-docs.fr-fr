---
title: 'IDebugCoreServer3 :: EnableAutoAttach | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732908"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Active l’attachement automatique pour les moteurs de débogage spécifiés.

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
dans Tableau de GUID pour chaque moteur de débogage à marquer comme attachement automatique.

`celtSpecificEngines`\
dans Nombre de moteurs spécifiés dans `rgguidSpecificEngines` .

`pszStartPageUrl`\
dans URL de début à utiliser lors de l’attachement automatique.

`pbstrSessionID`\
à ID de la session qui a été attachée automatiquement.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur. Un code d’erreur est `E_AUTO_ATTACH_NOT_REGISTERED` , qui indique que la fabrique de classe d’attachement automatique n’a pas été inscrite.

## <a name="remarks"></a>Notes
 Lorsqu’un programme associé à l’URL spécifiée est démarré, les moteurs de débogage spécifiés sont automatiquement démarrés et attachés.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
