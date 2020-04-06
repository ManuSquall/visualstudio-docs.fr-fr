---
title: Fonction SccBackgroundGet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701228"
---
# <a name="sccbackgroundget-function"></a>Fonction SccBackgroundGet
Cette fonction récupère à partir du contrôle source de chacun des fichiers spécifiés sans interaction utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 nFiles

[dans] Nombre de fichiers `lpFileNames` spécifiés dans le tableau.

 lpFileNames

[dans, dehors] Array de noms de fichiers à récupérer.

> [!NOTE]
> Les noms doivent être des noms de fichiers locaux entièrement qualifiés.

 dwFlags

[dans] Drapeaux de`SCC_GET_ALL` `SCC_GET_RECURSIVE`commande ( , ).

 dwBackgroundOperationID dwBackgroundOperationID

[dans] Une valeur unique associée à cette opération.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Opération exécutée avec succès.|
|SCC_E_BACKGROUNDGETINPROGRESS|Une récupération de fond est déjà en cours (le plug-in de contrôle source ne devrait le retourner que s’il ne prend pas en charge les opérations par lots simultanées).|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant d’être terminée.|

## <a name="remarks"></a>Notes
 Cette fonction est toujours appelée sur un thread différent de celui qui a chargé le plug-in de contrôle source. On ne s’attend pas à ce que cette fonction revienne tant qu’elle n’est pas terminée; cependant, il peut être appelé plusieurs fois avec plusieurs listes de fichiers, le tout en même temps.

 L’utilisation `dwFlags` de l’argument est la même que la [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
