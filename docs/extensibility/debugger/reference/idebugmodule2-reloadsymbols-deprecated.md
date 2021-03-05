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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d07f80a3dccef666c0608d79505816f73ff52013
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150521"
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
