---
title: Méthode Getautoinsertextensions,
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931524"
---
# <a name="getautoinsertextensions-method"></a>Méthode Getautoinsertextensions,
  Obtient des informations sur les applications pour Office qui doivent être insérées automatiquement pendant le débogage.

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
|*psaExtensionNames*|Noms d’extension des applications pour Office.|

## <a name="return-value"></a>Valeur retournée
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Chaque application pour Office à insérer est retournée sous la forme d’un nom d’extension d’application Office, qui correspond à une valeur sous **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L’hôte doit rechercher ces valeurs dans le registre, puis insérer automatiquement les extensions.
