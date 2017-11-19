---
title: Fonction de SccCloseProject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCloseProject
helpviewer_keywords: SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d37dc9bff7652856109fb4ec29c8eaa52f1d2507
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le projet a été correctement fermé.|  
|SCC_E_PROJNOTOPEN|Aucun projet n’est actuellement ouvert.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Remarques  
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelée avant cette fonction. Un appel à cette fonction est ensuite suivi d’un appel à la `SccOpenProject` fonction ou le [SccUninitialize](../extensibility/sccuninitialize-function.md), qui termine complètement la connexion au système de contrôle de code source.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)