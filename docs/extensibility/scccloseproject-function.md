---
title: SccCloseProject fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701047"
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

## <a name="remarks"></a>Notes
 Le [SccOpenProject](../extensibility/sccopenproject-function.md) est toujours appelé avant cette fonction. Un appel à cette fonction est ensuite suivi d’un appel à la `SccOpenProject` fonction ou à [SccUninitialize](../extensibility/sccuninitialize-function.md), qui met complètement fin à la connexion au système de contrôle de code source.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
