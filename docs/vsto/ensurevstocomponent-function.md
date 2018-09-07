---
title: Ensurevstocomponent, fonction
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
ms.openlocfilehash: 08b22ed86851a35f23306fc765f62f265da4701e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671204"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent, fonction
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
  
## <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d’erreur.  
  
  