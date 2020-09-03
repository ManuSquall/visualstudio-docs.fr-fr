---
title: Ensurevstocomponent, fonction)
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
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543583"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent, fonction)
  Cette API prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pProject*|N’utilisez pas.|

## <a name="return-value"></a>Valeur retournée
 Si la fonction est réussie, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d'erreur.
