---
description: Obtient des informations sur les applications pour Office qui doivent être insérées automatiquement pendant le débogage.
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
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223431"
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
