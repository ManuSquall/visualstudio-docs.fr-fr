---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9eb8beed7f32e9c6fb64212f73a41a35544259bb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326970"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permet l’attachement automatique pour les moteurs de débogage spécifié.

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
[in] Tableau de GUID pour chaque moteur de débogage pour marquer comme l’attachement automatique.

`celtSpecificEngines`\
[in] Le nombre de moteurs spécifié dans `rgguidSpecificEngines`.

`pszStartPageUrl`\
[in] URL de démarrage à utiliser lors de l’attachement d’automatique.

`pbstrSessionID`\
[out] ID de la session qui a été attaché à automatique.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Un code d’erreur est `E_AUTO_ATTACH_NOT_REGISTERED`, ce qui indique que la fabrique de classe auto-attach n’a pas été inscrit.

## <a name="remarks"></a>Notes
 Lorsqu’un programme associé à l’URL spécifiée est démarré, les moteurs de débogage spécifié sont automatiquement démarrés et attachés.

## <a name="see-also"></a>Voir aussi
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)