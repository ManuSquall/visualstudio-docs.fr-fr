---
description: Cette fonction récupère, à partir du contrôle de code source, chacun des fichiers spécifiés sans intervention de l’utilisateur.
title: SccBackgroundGet fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 316a02e84b4d51f309aecdd98d0409c85ccbdbef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901238"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet fonction)
Cette fonction récupère, à partir du contrôle de code source, chacun des fichiers spécifiés sans intervention de l’utilisateur.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 Nfichiers

dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

[in, out] Tableau de noms des fichiers à récupérer.

> [!NOTE]
> Les noms doivent être des noms de fichiers locaux complets.

 dwFlags

dans Indicateurs de commande ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

dans Valeur unique associée à cette opération.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Opération exécutée avec succès.|
|SCC_E_BACKGROUNDGETINPROGRESS|Une récupération en arrière-plan est déjà en cours (le plug-in de contrôle de code source doit le retourner uniquement s’il ne prend pas en charge les opérations batch simultanées).|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant d’être terminée.|

## <a name="remarks"></a>Remarques
 Cette fonction est toujours appelée sur un thread différent de celui qui a chargé le plug-in de contrôle de code source. Cette fonction ne doit pas être retournée tant qu’elle n’est pas terminée ; Toutefois, elle peut être appelée plusieurs fois avec plusieurs listes de fichiers, en même temps.

 L’utilisation de l' `dwFlags` argument est identique à celle de [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
