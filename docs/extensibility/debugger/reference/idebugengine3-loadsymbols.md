---
title: 'IDebugEngine3 :: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f823f0087ee612a7850e000469271e0c2a778b62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887300"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Charge (si nécessaire) les symboles pour tous les modules en cours de débogage par ce moteur de débogage.

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
 En cas de réussite, retourne S_OK ; Sinon, retourne le code d’erreur.

## <a name="remarks"></a>Remarques
 Cela charge les symboles de débogage pour tous les modules référencés par ce moteur de débogage. Les symboles sont chargés uniquement s’ils n’ont pas encore été chargés. Les symboles sont recherchés sur les chemins d’accès définis par un appel à [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Voir aussi
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
