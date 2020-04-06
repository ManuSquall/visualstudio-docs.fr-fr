---
title: Fonction SccAddDeDeScc (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701248"
---
# <a name="sccaddfromscc-function"></a>Fonction SccAddDeDeScc
Cette fonction permet à l’utilisateur de parcourir les fichiers qui sont déjà dans le système de contrôle source et ensuite faire de ces fichiers une partie du projet en cours. Par exemple, cette fonction peut obtenir un fichier d’en-tête commun dans le projet en cours sans copier le fichier. Le tableau de `lplpFileNames`retour des fichiers, contient la liste des fichiers que l’utilisateur veut ajouter au projet IDE.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpnFiles (lpnFiles)

[dans, dehors] Un tampon pour le nombre de fichiers qui sont ajoutés. (C’est `NULL` si la `lplpFileNames` mémoire pointée par doit être libérée. Voir Remarques pour plus de détails.)

 lplpFileNames lplpFileNames lplpFileNames lpl

[dans, dehors] Un tableau de pointeurs à tous les noms de fichiers sans parcours d’annuaire. Ce tableau est attribué et libéré par le plug-in de contrôle source. Si `lpnFiles` le numéro `lplpFileNames` 1 et n’est `NULL`pas, `lplpFileNames` le prénom dans le tableau indiqué par contient le dossier de destination.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Les dossiers ont été localisés avec succès et ajoutés au projet.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée sans effet.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|

## <a name="remarks"></a>Notes
 L’IDE appelle cette fonction. Si le plug-in de contrôle source prend en charge `lpnFiles` la spécifation d’un `lplpFileNames`dossier de destination local, l’IDE passe 1 et passe le nom du dossier local en .

 Lorsque l’appel `SccAddFromScc` à la fonction revient, `lpnFiles` le `lplpFileNames`plug-in a attribué des valeurs à et, allouant la `lplpFileNames`mémoire pour le tableau de nom de fichier si nécessaire (notez que cette allocation remplace le pointeur dans ). Le plug-in de contrôle source est responsable de placer tous les fichiers dans l’annuaire de l’utilisateur ou dans le dossier de désignation spécifié. L’IDE ajoute ensuite les fichiers au projet IDE.

 Enfin, l’IDE appelle cette fonction `NULL` une `lpnFiles`deuxième fois, en passant pour . Ceci est interprété comme un signal spécial par le plug-in de contrôle source pour libérer la mémoire allouée pour le tableau de nom de fichier dans`lplpFileNames``.`

 `lplpFileNames`est `char ***` un pointeur. Le plug-in de contrôle source place un pointeur à un tableau de pointeurs pour classer les noms, passant ainsi la liste de la manière standard pour cette API.

> [!NOTE]
> Les versions initiales de l’API VSSCI n’ont pas fourni de moyen d’indiquer le projet cible pour les fichiers ajoutés. Pour tenir compte de cela, `lplpFIleNames` la sémantique du paramètre ont été améliorées pour en faire un paramètre in/out plutôt qu’un paramètre de sortie. Si un seul fichier est spécifié, c’est-à-dire la valeur indiquée par `lpnFiles` le premier élément de `lplpFileNames` contient le dossier cible. Pour utiliser ces nouvelles sémantiques, `SccSetOption` l’IDE appelle la fonction avec le `nOption`paramètre défini à `SCC_OPT_SHARESUBPROJ`. Si un plug-in de contrôle source ne prend `SCC_E_OPTNOTSUPPORTED`pas en charge la sémantique, il revient. Cela désactive l’utilisation de la fonction **Add from Source Control.** Si un plug-in prend en charge la fonction **Add from Source Control** (`SCC_CAP_ADDFROMSCC`), alors il doit prendre en charge la nouvelle sémantique et le retour `SCC_I_SHARESUBPROJOK`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
