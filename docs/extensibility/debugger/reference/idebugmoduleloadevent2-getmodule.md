---
description: Obtient le module en cours de chargement ou de déchargement.
title: 'IDebugModuleLoadEvent2 :: GetModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4605b5eab9137fd918238143d8f0453f9f8c54b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065370"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtient le module en cours de chargement ou de déchargement.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Paramètres
`pModule`\
à Retourne un objet [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) qui représente le module en cours de chargement ou de déchargement.

`pbstrDebugMessage`\
[in, out] Retourne un message facultatif qui décrit cet événement. Si ce paramètre est une valeur null, aucun message n’est demandé.

`pbLoad`\
[in, out] Différent de zéro ( `TRUE` ) si le module est en cours de chargement et zéro ( `FALSE` ) si le module est en cours de déchargement. Si ce paramètre est une valeur null, aucun État n’est demandé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
