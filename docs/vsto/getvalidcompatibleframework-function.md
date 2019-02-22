---
title: Getvalidcompatibleframework, fonction
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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643507"
---
# <a name="getvalidcompatibleframework-function"></a>Getvalidcompatibleframework, fonction
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
 Si la fonction réussit, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d’erreur.
