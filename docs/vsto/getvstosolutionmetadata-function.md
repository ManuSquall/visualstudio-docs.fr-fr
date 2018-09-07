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
ms.openlocfilehash: e6289a0d19bc6621d98edfc974ad265791876a70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673636"
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
  
  