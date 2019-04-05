---
title: Fonction SccCloseProject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953332"
---
# <a name="scccloseproject-function"></a>Fonction SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction ferme un projet, en marquant la fin d’une session particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 La structure de contexte de plug-in de contrôle de source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le projet a été correctement fermé.|  
|SCC_E_PROJNOTOPEN|Aucun projet n’est actuellement ouvert.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelée avant cette fonction. Un appel à cette fonction est ensuite suivi par un appel à la `SccOpenProject` (fonction) ou le [SccUninitialize](../extensibility/sccuninitialize-function.md), qui termine complètement la connexion au système de contrôle source.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
