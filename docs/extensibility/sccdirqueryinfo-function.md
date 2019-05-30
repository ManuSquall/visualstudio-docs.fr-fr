---
title: Fonction SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e19b65ea4b3c4cd87b1f9d6a3db9e6f8ae64d16d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332241"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo function
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

[in] La structure de contexte de plug-in de contrôle de source.

 nDirs

[in] Le nombre de répertoires sélectionnés à interroger.

 lpDirNames

[in] Un tableau des chemins qualifiés complets des répertoires à interroger.

 lpStatus

[in, out] Une structure de tableau pour le plug-in pour retourner les indicateurs d’état de contrôle de code source (consultez [code d’état Directory](../extensibility/directory-status-code-enumerator.md) pour plus d’informations).

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|La requête a réussi.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|

## <a name="remarks"></a>Notes
 La fonction remplit le tableau de résultats avec un masque de bits de bits à partir de la `SCC_DIRSTATUS` famille (consultez [code d’état Directory](../extensibility/directory-status-code-enumerator.md)), une entrée pour chaque répertoire donné. Le tableau de statut est alloué par l’appelant.

 L’IDE utilise cette fonction avant qu’un répertoire est renommé pour vérifier si le répertoire est sous contrôle de code source en interrogeant si elle possède un projet correspondant. Si le répertoire n’est pas sous contrôle de code source, l’IDE peut fournir l’avertissement approprié à l’utilisateur.

> [!NOTE]
> Si un plug-in de contrôle de code source choisit de n'implémenter pas une ou plusieurs valeurs d’état, non implémentées bits doivent être définis sur zéro.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’état de répertoire](../extensibility/directory-status-code-enumerator.md)