---
title: Fonction SccGetProjPath (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700702"
---
# <a name="sccgetprojpath-function"></a>Fonction SccGetProjPath
Cette fonction invite l’utilisateur pour un chemin de projet, qui est une chaîne qui n’est significative que pour le plug-in de contrôle source. Il est appelé lorsque l’utilisateur est:

- Création d’un projet

- Ajout d’un projet existant au contrôle de la version

- Tenter de trouver un projet de contrôle de version existant

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[dans, dehors] Le nom d’utilisateur (ne pas dépasser SCC_USER_SIZE, y compris le terminateur NULL)

 lpProjName

[dans, dehors] Le nom du projet IDE, l’espace de travail du projet ou makefile (à ne pas dépasser SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpLocalPath (en)

[dans, dehors] Le chemin de travail du projet. Si `bAllowChangePath` `TRUE`c’est le cas, le plug-in de contrôle source peut modifier cette chaîne (ne pas dépasser _MAX_PATH, y compris le null-terminateur).

 lpAuxProjPath

[dans, dehors] Un tampon pour le chemin retourné du projet (ne pas dépasser SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 bAllowChangePath (en)

[dans] Si c’est `TRUE`le cas, le plug-in `lpLocalPath` de contrôle source peut inciter et modifier la chaîne.

 pbNew

[dans, dehors] La valeur à venir indique s’il faut créer un nouveau projet. La valeur retournée indique le succès de la création d’un projet :

|Entrant|Interprétation|
|--------------|--------------------|
|TRUE|L’utilisateur peut créer un nouveau projet.|
|FALSE|L’utilisateur ne peut pas créer un nouveau projet.|

|Sortant|Interprétation|
|--------------|--------------------|
|TRUE|Un nouveau projet a été créé.|
|FALSE|Un projet existant a été sélectionné.|

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le projet a été créé ou récupéré avec succès.|
|SCC_I_OPERATIONCANCELED|L'opération a été annulée.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|Il y avait un problème à essayer de se connecter au système de contrôle source.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|

## <a name="remarks"></a>Notes
 Le but de cette fonction est que l’IDE acquiert les paramètres `lpProjName` et `lpAuxProjPath`. Une fois que le plug-in de contrôle source invite l’utilisateur pour ces informations, il passe ces deux chaînes de nouveau à l’IDE. L’IDE persiste ces chaînes dans son fichier de solution et les transmet au [SccOpenProject](../extensibility/sccopenproject-function.md) chaque fois que l’utilisateur ouvre ce projet. Ces chaînes permettent au plug-in de suivre les informations associées à un projet.

 Lorsque la fonction est `lpAuxProjPath` appelée pour la première fois, est réglée à une chaîne vide. `lProjName`peut également être vide, ou il peut contenir le nom du projet IDE, que le plug-in de contrôle source peut utiliser ou ignorer. Lorsque la fonction revient avec succès, le plug-in renvoie les deux chaînes correspondantes. L’IDE ne fait aucune hypothèse sur ces chaînes, ne les utilisera pas et ne permettra pas à l’utilisateur de les modifier. Si l’utilisateur veut modifier les paramètres, `SccGetProjPath` l’IDE appellera à nouveau, en passant dans les mêmes valeurs qu’il avait reçues la fois précédente. Cela donne le plug-in contrôle complet sur ces deux cordes.

 Pour `lpUser`, l’IDE peut passer dans un nom d’utilisateur, ou il peut simplement passer dans un pointeur à une chaîne vide. S’il y a un nom d’utilisateur, le plug-in de contrôle source doit l’utiliser par défaut. Toutefois, si aucun nom n’a été adopté ou si la connexion a échoué avec le nom donné, `lpUser` le plug-in devrait inciter l’utilisateur pour une connexion et passer le nom de retour quand il reçoit une connexion valide. Étant donné que le plug-in peut modifier cette chaîne, l’IDE allouera toujours un tampon de taille (no`SCC_USER_LEN`1).

> [!NOTE]
> La première action que l’IDE effectue peut `SccOpenProject` être `SccGetProjPath` un appel à la fonction ou à la fonction. Par conséquent, les deux `lpUser` ont un paramètre identique, ce qui permet au plug-in de contrôle source de connecter l’utilisateur à chaque moment. Même si le retour de la fonction indique une défaillance, le plug-in doit remplir cette chaîne avec un nom de connexion valide.

 `lpLocalPath`est l’annuaire où l’utilisateur garde le projet. C’est peut-être une ficelle vide. S’il n’y a pas d’annuaire actuellement défini (comme dans le cas `bAllowChangePath` d’un utilisateur essayant de télécharger un projet à partir du système de contrôle source) et si c’est le cas, `TRUE`le plug-in de contrôle source peut inciter l’utilisateur à entrer ou utiliser une autre méthode pour placer sa propre chaîne dans `lpLocalPath`. Si `bAllowChangePath` `FALSE`c’est le cas, le plug-in ne doit pas changer la chaîne, car l’utilisateur travaille déjà dans l’annuaire spécifié.

 Si l’utilisateur crée un nouveau projet à mettre sous contrôle source, le plug-in de `SccGetProjPath` contrôle source pourrait ne pas réellement le créer dans le système de contrôle source à l’époque est appelé. Au lieu de cela, il passe en `pbNew`arrière la chaîne avec une valeur non zéro pour , indiquant que le projet sera créé dans le système de contrôle source.

 Par exemple, si un utilisateur de **l’assistant New Project** de Visual Studio ajoute son projet au contrôle source, Visual Studio appelle cette fonction, et le plug-in détermine s’il est acceptable de créer un nouveau projet dans le système de contrôle source pour contenir le projet Visual Studio. Si l’utilisateur clique **Annuler** avant de terminer l’assistant, le projet n’est jamais créé. Si l’utilisateur clique **sur OK,** Visual Studio appelle, `SccOpenProject`passant, `SCC_OPT_CREATEIFNEW`et le projet contrôlé par la source est créé à ce moment-là.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
