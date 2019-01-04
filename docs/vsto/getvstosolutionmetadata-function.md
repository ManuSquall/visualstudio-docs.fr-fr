---
title: Getvstosolutionmetadata, fonction
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0cb0acd57ff04b7487d5311f8a05219b3ce0c0a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853721"
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
