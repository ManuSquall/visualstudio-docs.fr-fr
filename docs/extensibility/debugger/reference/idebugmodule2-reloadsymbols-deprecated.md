---
title: IDebugModule2:ReloadSymbols_Deprecated Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726921"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLÈTE. NE PAS UTILISER. Recharge les symboles de ce module.

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
[dans] Le chemin vers le magasin de symboles.

`pbstrDebugMessage`\
[out] Renvoie un message d’information, tel qu’un message d’état ou d’erreur, qui s’affiche à droite du nom du module dans la fenêtre modules.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Un moteur de débogé doit toujours revenir `E_FAIL`.

## <a name="remarks"></a>Notes
 Cette méthode n’est plus prise en charge. Implémenter la méthode [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) à la place.

## <a name="see-also"></a>Voir aussi
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
