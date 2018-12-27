---
title: Getvstosolutionmetadata, fonction
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: baa5cf48d317da80f78d19a1b72f81824b1bed62
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647264"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata, fonction
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
  
## <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d’erreur.  
  
  