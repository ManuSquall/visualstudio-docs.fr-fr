---
description: Envoie la chaîne de message spécifiée à la fenêtre de sortie du débogueur.
title: IDebugIDECallback ::D isplayMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6968c524559280756014bb6b26f55f688bc38ab3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091940"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Envoie la chaîne de message spécifiée à la fenêtre de sortie du débogueur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisplayMessage (
   LPCOLESTR szMessage
);
```

```csharp
int DisplayMessage (
   string szMessage
);
```

## <a name="parameters"></a>Paramètres
`szMessage`\
dans Chaîne de message à afficher dans la fenêtre de sortie du débogueur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
