---
title: IDebugEngine3:LoadSymbols Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730810"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Des charges (au besoin) des symboles pour tous les modules déboqués par ce moteur de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; retourne autrement le code d’erreur.

## <a name="remarks"></a>Notes
 Cela charge les symboles de débogage pour tous les modules référencés par ce moteur de débogage. Les symboles ne sont chargés que s’ils n’ont pas déjà été chargés. Les symboles sont recherchés sur les chemins fixés par un appel à [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Voir aussi
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
