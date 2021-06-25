---
description: Cette fonction ferme un projet et marque la fin d’une session particulière.
title: SccCloseProject fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904693"
---
# <a name="scccloseproject-function"></a>SccCloseProject fonction)
Cette fonction ferme un projet et marque la fin d’une session particulière.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Paramètres
 pvContext la structure du contexte du plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le projet a été correctement fermé.|
|SCC_E_PROJNOTOPEN|Aucun projet n’est actuellement ouvert.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelé avant cette fonction. Un appel à cette fonction est ensuite suivi d’un appel à la `SccOpenProject` fonction ou à [SccUninitialize](../extensibility/sccuninitialize-function.md), qui met complètement fin à la connexion au système de contrôle de code source.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
