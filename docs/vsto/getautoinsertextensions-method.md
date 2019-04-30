---
title: Getautoinsertextensions, méthode
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972276"
---
# <a name="getautoinsertextensions-method"></a>Getautoinsertextensions, méthode
  Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.

 Cette méthode est réservée à une utilisation ultérieure.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*psaExtensionNames*|Les noms d’extension des applications pour Office.|

## <a name="return-value"></a>Valeur de retour
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Chaque application pour Office doit être inséré est retournée comme un nom d’extension application Office, ce qui correspond à une valeur sous **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L’hôte doit rechercher ces valeurs dans le Registre et puis insère automatiquement les extensions.
