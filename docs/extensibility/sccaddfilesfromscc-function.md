---
title: SccAddFilesDeSCC Fonction (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701286"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesDeSCC fonction
Cette fonction ajoute une liste de fichiers allant du contrôle source au projet actuellement ouvert.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[dans, dehors] Le nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris le terminateur nul).

 lpAuxProjPath

[dans, dehors] Chaîne auxiliaire identifiant le `SCC_PRJPATH_`projet (jusqu’à SIZE, y compris le terminateur nul).

 cFiles

[dans] Nombre de fichiers `lpFilePaths`donnés par .

 lpFilePaths

[dans, dehors] Array de noms de fichiers à ajouter au projet en cours.

 lpDestination

[dans] Le chemin de destination où les fichiers doivent être écrits.

 lpComment

[dans] Le commentaire à appliquer à chacun des fichiers ajoutés.

 pbResults

[dans, dehors] Array de drapeaux qui sont réglés pour indiquer le succès (nonzero ou VRAI) ou l’échec (zéro ou FALSE) pour chaque fichier (la taille du tableau doit être au moins `cFiles` long).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert.|
|SCC_E_OPNOTPERFORMED|La connexion n’est pas au même projet que spécifié par`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à mettre à jour la base de données.|
|SCC_E_NONSPECIFICERROR|Erreur inconnue.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
