---
title: Méthode Getautoinsertextensions,
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543505"
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

## <a name="return-value"></a>Valeur renvoyée
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Remarques
 Chaque application pour Office à insérer est retournée sous la forme d’un nom d’extension d’application Office, qui correspond à une valeur sous **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**. L’hôte doit rechercher ces valeurs dans le registre, puis insérer automatiquement les extensions.
