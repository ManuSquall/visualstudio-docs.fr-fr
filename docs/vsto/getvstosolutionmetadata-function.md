---
title: Getvstosolutionmetadata, fonction)
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
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520183"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata, fonction)
  Cette API prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|N’utilisez pas.|
|*ppSolutionInfo*|N’utilisez pas.|

## <a name="return-value"></a>Valeur renvoyée
 Si la fonction est réussie, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d'erreur.
