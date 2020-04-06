---
title: IDebugModule3::LoadSymbols Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726772"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Charge les symboles pour le module actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Valeur de retour
 Si la méthode réussit, retourne `S_OK`. En cas d'échec, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode charge les symboles du chemin de recherche actuel (qui peut être modifié en appelant la méthode [SetSymbolPath).](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

 Cette méthode est préférée à la [méthode ReloadSymbols_Deprecated.](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)

## <a name="see-also"></a>Voir aussi
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
