---
description: OBSOLÈTE. Recharge les symboles pour ce module.
title: 'IDebugModule2 :: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dfcd1edd92048cde6da6cc195c3e0ba8f1cd392
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065708"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLÈTE. N’UTILISEZ PAS. Recharge les symboles pour ce module.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Paramètres
`pszUrlToSymbols`\
dans Chemin d’accès au magasin de symboles.

`pbstrDebugMessage`\
à Retourne un message d’information, tel qu’un État ou un message d’erreur, qui s’affiche à droite du nom du module dans la fenêtre modules.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Un moteur de débogage doit toujours retourner `E_FAIL` .

## <a name="remarks"></a>Notes
 Cette méthode n’est plus prise en charge. Implémentez la méthode [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) à la place.

## <a name="see-also"></a>Voir aussi
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
