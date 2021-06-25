---
description: Cette fonction examine une liste de répertoires complets pour leur état actuel.
title: SccDirQueryInfo fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9a3e65fa03c7fc2b6a8ce83ba2bb39250547aadb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904615"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo fonction)
Cette fonction examine une liste de répertoires complets pour leur état actuel.

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

dans Structure de contexte du plug-in de contrôle de code source.

 nDirs

dans Nombre de répertoires sélectionnés à interroger.

 lpDirNames

dans Tableau de chemins d’accès qualifiés complets des répertoires à interroger.

 lpStatus

[in, out] Structure de tableau pour que le plug-in de contrôle de code source retourne les indicateurs d’État (pour plus d’informations, consultez le [code d’État du répertoire](../extensibility/directory-status-code-enumerator.md) ).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La requête a réussi.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 La fonction remplit le tableau de retour avec un masque de bits de la `SCC_DIRSTATUS` famille (voir [code d’État du répertoire](../extensibility/directory-status-code-enumerator.md)), une entrée pour chaque répertoire donné. Le tableau d’État est alloué par l’appelant.

 L’IDE utilise cette fonction avant qu’un répertoire ne soit renommé afin de vérifier si le répertoire est sous contrôle de code source en interrogeant s’il possède un projet correspondant. Si le répertoire n’est pas sous contrôle de code source, l’IDE peut fournir l’avertissement approprié à l’utilisateur.

> [!NOTE]
> Si un plug-in de contrôle de code source choisit de ne pas implémenter une ou plusieurs des valeurs d’État, les bits non implémentés doivent avoir la valeur zéro.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’État du répertoire](../extensibility/directory-status-code-enumerator.md)
