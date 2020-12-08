---
title: Getvalidcompatibleframework, fonction)
description: Découvrez comment l’API Getvalidcompatibleframework, prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement à partir de votre code.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 96f536b3ab8e28b87a59a637fcf6dbaadeb21bf7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845074"
---
# <a name="getvalidcompatibleframework-function"></a>Getvalidcompatibleframework, fonction)
  Cette API prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|N’utilisez pas.|
|*pbstrValidFrameworkTag*|N’utilisez pas.|

## <a name="return-value"></a>Valeur de retour
 Si la fonction est réussie, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d'erreur.
