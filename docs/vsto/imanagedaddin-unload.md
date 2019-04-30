---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956742"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Appelée juste avant qu’un complément VSTO managé soit déchargé.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valeur de retour
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Cette méthode n’est pas appelée par les versions actuelles de Microsoft Office. Cette méthode est réservée à une utilisation ultérieure.

## <a name="see-also"></a>Voir aussi
- [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
