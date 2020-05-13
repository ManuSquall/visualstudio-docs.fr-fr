---
title: Fonction SccDirQueryInfo (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700951"
---
# <a name="sccdirqueryinfo-function"></a>Fonction SccDirQueryInfo
Cette fonction examine une liste d’annuaires entièrement qualifiés pour leur statut actuel.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] La structure de contexte de plug-in de contrôle de source.

 nDirs (nDirs)

[dans] Le nombre d’annuaires sélectionnés pour être interrogés.

 lpDirNames (en)

[dans] Un éventail de chemins entièrement qualifiés des répertoires à interroger.

 lpStatus

[dans, dehors] Une structure de tableau pour le plug-in de contrôle source pour retourner les drapeaux d’état (voir [code d’état d’annuaire](../extensibility/directory-status-code-enumerator.md) pour plus de détails).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La requête a été couronnée de succès.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle du code source ne prend pas en charge cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 La fonction remplit le tableau de retour avec un `SCC_DIRSTATUS` peu de bits de la famille (voir [code de statut répertoire](../extensibility/directory-status-code-enumerator.md)), une entrée pour chaque répertoire donné. Le tableau d’état est attribué par l’appelant.

 L’IDE utilise cette fonction avant qu’un répertoire ne soit renommé pour vérifier si l’annuaire est sous contrôle source en se demandait s’il a un projet correspondant. Si l’annuaire n’est pas sous contrôle source, l’IDE peut fournir l’avertissement approprié à l’utilisateur.

> [!NOTE]
> Si un plug-in de contrôle source choisit de ne pas implémenter une ou plusieurs valeurs de statut, les bits non mis en œuvre doivent être réglés à zéro.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’état de l’annuaire](../extensibility/directory-status-code-enumerator.md)
