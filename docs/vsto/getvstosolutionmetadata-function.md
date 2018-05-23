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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d21b0d2b90441f0b9be543933e7243dd41440b02
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata, fonction
  Cette API prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```c  
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
  
  