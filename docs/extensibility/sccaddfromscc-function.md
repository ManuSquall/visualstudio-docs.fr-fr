---
description: Cette fonction permet à l’utilisateur de rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis de faire de ces fichiers une partie du projet actuel.
title: SccAddFromScc fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904874"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc fonction)
Cette fonction permet à l’utilisateur de rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis de faire de ces fichiers une partie du projet actuel. Par exemple, cette fonction peut obtenir un fichier d’en-tête commun dans le projet actif sans copier le fichier. Le tableau de retour des fichiers, `lplpFileNames` , contient la liste des fichiers que l’utilisateur souhaite ajouter au projet IDE.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpnFiles

[in, out] Mémoire tampon pour le nombre de fichiers qui sont ajoutés dans. (C’est `NULL` le cas si la mémoire pointée par `lplpFileNames` doit être libérée. Pour plus d’informations, consultez la section Notes.)

 lplpFileNames

[in, out] Tableau de pointeurs vers tous les noms de fichiers sans chemins d’accès aux répertoires. Ce tableau est alloué et libéré par le plug-in de contrôle de code source. Si `lpnFiles` = 1 et `lplpFileNames` n’est pas `NULL` , le premier nom dans le tableau pointé par `lplpFileNames` contient le dossier de destination.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Les fichiers ont été correctement localisés et ajoutés au projet.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée sans effet.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|

## <a name="remarks"></a>Remarques
 L’IDE appelle cette fonction. Si le plug-in de contrôle de code source prend en charge la spécification d’un dossier de destination local, l’IDE passe `lpnFiles` à 1 et transmet le nom du dossier local dans `lplpFileNames` .

 Lorsque l’appel à la `SccAddFromScc` fonction retourne, le plug-in a affecté des valeurs à `lpnFiles` et `lplpFileNames` , en allouant la mémoire pour le tableau de noms de fichiers si nécessaire (Notez que cette allocation remplace le pointeur dans `lplpFileNames` ). Le plug-in de contrôle de code source est chargé de placer tous les fichiers dans le répertoire de l’utilisateur ou dans le dossier de désignation spécifié. L’IDE ajoute ensuite les fichiers au projet IDE.

 Enfin, l’IDE appelle cette fonction une deuxième fois, en passant `NULL` pour `lpnFiles` . Cela est interprété comme un signal spécial par le plug-in de contrôle de code source pour libérer la mémoire allouée pour le tableau de noms de fichiers dans `lplpFileNames``.`

 `lplpFileNames` est un `char ***` pointeur. Le plug-in de contrôle de code source place un pointeur vers un tableau de pointeurs vers des noms de fichiers, transmettant ainsi la liste de manière standard pour cette API.

> [!NOTE]
> Les versions initiales de l’API VSSCI n’offraient pas de moyen d’indiquer le projet cible pour les fichiers ajoutés. Pour ce faire, la sémantique du `lplpFIleNames` paramètre a été améliorée pour en faire un paramètre in/out plutôt qu’un paramètre de sortie. Si un seul fichier est spécifié, autrement dit, la valeur désignée par `lpnFiles` = 1, le premier élément de `lplpFileNames` contient le dossier cible. Pour utiliser cette nouvelle sémantique, l’IDE appelle la `SccSetOption` fonction avec le `nOption` paramètre défini sur `SCC_OPT_SHARESUBPROJ` . Si un plug-in de contrôle de code source ne prend pas en charge la sémantique, il retourne `SCC_E_OPTNOTSUPPORTED` . Cela désactive l’utilisation de la fonctionnalité **Ajouter à partir du contrôle de code source** . Si un plug-in prend en charge la fonctionnalité **Ajouter à partir du contrôle de code source** ( `SCC_CAP_ADDFROMSCC` ), il doit prendre en charge la nouvelle sémantique et retourner `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
