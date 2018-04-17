---
title: Fonction de SccCloseProject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f977c1241408f5e33d31a63262abb5ee24670e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="scccloseproject-function"></a>SccCloseProject (fonction)
Cette fonction ferme un projet, marquant la fin d’une session particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 La structure de contexte plug-in de contrôle de code source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le projet a été correctement fermé.|  
|SCC_E_PROJNOTOPEN|Aucun projet n’est actuellement ouvert.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelée avant cette fonction. Un appel à cette fonction est ensuite suivi d’un appel à la `SccOpenProject` fonction ou le [SccUninitialize](../extensibility/sccuninitialize-function.md), qui termine complètement la connexion au système de contrôle de code source.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)