---
description: Cette fonction ajoute une liste de fichiers du contrôle de code source au projet actuellement ouvert.
title: SccAddFilesFromSCC fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fa08ec93383fa661d1e2dd055b3139b2ba90f34
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904862"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC fonction)
Cette fonction ajoute une liste de fichiers du contrôle de code source au projet actuellement ouvert.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris la marque de fin null).

 lpAuxProjPath

[in, out] Chaîne auxiliaire identifiant le projet ( `SCC_PRJPATH_` taille maximale, y compris la marque de fin null).

 cFiles

dans Nombre de fichiers spécifiés par `lpFilePaths` .

 lpFilePaths

[in, out] Tableau de noms de fichiers à ajouter au projet en cours.

 lpDestination

dans Chemin d’accès de destination où les fichiers doivent être écrits.

 lpComment

dans Commentaire à appliquer à chacun des fichiers ajoutés.

 pbResults

[in, out] Tableau d’indicateurs qui sont définis pour indiquer la réussite (valeur différente de zéro ou TRUE) ou l’échec (zéro ou FALSe) pour chaque fichier (la taille du tableau doit être au moins `cFiles` longue).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert.|
|SCC_E_OPNOTPERFORMED|La connexion n’est pas vers le même projet que celui spécifié par `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à mettre à jour la base de données.|
|SCC_E_NONSPECIFICERROR|Erreur inconnue.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
