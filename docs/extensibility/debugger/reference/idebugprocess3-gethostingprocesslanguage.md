---
title: IDebugProcess3::GetHostingProcessLanguage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b27be0850755a1a2808c8c5c758a3ad59b41d7e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723616"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Cette méthode `GUID` renvoie une représentation de la langue de ce processus tel qu’il est fixé par un appel à [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Paramètres
`pguidLang`\
[out] Le `GUID` langage de ce processus. `GUID_NULL`(C) ou `Guid.Empty` (C) signifie que la langue n’est pas définie.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
