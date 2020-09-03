---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
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
ms.openlocfilehash: 1ec01ebc32472e315fe2c905ecfd2cfef0f4bbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541009"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Appelée juste avant qu’un complément VSTO managé soit déchargé.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valeur retournée
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Cette méthode n’est pas appelée par les versions actuelles de Microsoft Office. Cette méthode est réservée à une utilisation ultérieure.

## <a name="see-also"></a>Voir aussi
- [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddIn::Load](../vsto/imanagedaddin-load.md)
