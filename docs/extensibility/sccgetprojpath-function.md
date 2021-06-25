---
description: Cette fonction invite l’utilisateur à entrer un chemin d’accès au projet, qui est une chaîne qui est significative uniquement pour le plug-in de contrôle de code source.
title: SccGetProjPath fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901069"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath fonction)
Cette fonction invite l’utilisateur à entrer un chemin d’accès au projet, qui est une chaîne qui est significative uniquement pour le plug-in de contrôle de code source. Elle est appelée lorsque l’utilisateur est :

- Création d’un projet

- Ajout d’un projet existant au contrôle de version

- Tentative de recherche d’un projet de contrôle de version existant

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Nom d’utilisateur (à ne pas dépasser SCC_USER_SIZE, y compris la marque de fin NULL)

 lpProjName

[in, out] Nom du projet IDE, de l’espace de travail du projet ou du Makefile (à ne pas dépasser SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpLocalPath

[in, out] Chemin d’accès de travail du projet. Si `bAllowChangePath` a `TRUE` la valeur, le plug-in de contrôle de code source peut modifier cette chaîne (sans dépasser _MAX_PATH, y compris la marque de fin null).

 lpAuxProjPath

[in, out] Mémoire tampon pour le chemin d’accès du projet retourné (à ne pas dépasser SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 bAllowChangePath

dans Si c’est `TRUE` le cas, le plug-in de contrôle de code source peut demander et modifier la `lpLocalPath` chaîne.

 pbNew

[in, out] La valeur entrante indique s’il faut créer un nouveau projet. La valeur retournée indique la réussite de la création d’un projet :

|Entrant|Interprétation|
|--------------|--------------------|
|true|L’utilisateur peut créer un nouveau projet.|
|FALSE|L’utilisateur ne peut pas créer un nouveau projet.|

|Sortant|Interprétation|
|--------------|--------------------|
|true|Un nouveau projet a été créé.|
|FALSE|Un projet existant a été sélectionné.|

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le projet a été correctement créé ou récupéré.|
|SCC_I_OPERATIONCANCELED|L'opération a été annulée.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|Un problème est survenu lors de la tentative de connexion au système de contrôle de code source.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|

## <a name="remarks"></a>Remarques
 L’objectif de cette fonction est que l’IDE obtienne les paramètres `lpProjName` et `lpAuxProjPath` . Une fois que le plug-in de contrôle de code source demande ces informations à l’utilisateur, il transmet ces deux chaînes à l’IDE. L’IDE conserve ces chaînes dans son fichier solution et les transmet à [SccOpenProject](../extensibility/sccopenproject-function.md) chaque fois que l’utilisateur ouvre ce projet. Ces chaînes permettent au plug-in de suivre les informations associées à un projet.

 Lorsque la fonction est appelée pour la première fois, la `lpAuxProjPath` valeur est une chaîne vide. `lProjName` peut également être vide ou contenir le nom du projet IDE, que le plug-in de contrôle de code source peut utiliser ou ignorer. Quand la fonction retourne avec succès, le plug-in retourne les deux chaînes correspondantes. L’IDE n’émet aucune hypothèse sur ces chaînes, ne les utilise pas et n’autorise pas l’utilisateur à les modifier. Si l’utilisateur souhaite modifier les paramètres, l’environnement de développement intégré (IDE) rappellera les `SccGetProjPath` mêmes valeurs qu’il avait reçues l’heure précédente. Cela donne au plug-in un contrôle total sur ces deux chaînes.

 Pour `lpUser` , l’IDE peut passer un nom d’utilisateur ou il peut simplement passer un pointeur vers une chaîne vide. S’il existe un nom d’utilisateur, le plug-in de contrôle de code source doit l’utiliser comme valeur par défaut. Toutefois, si aucun nom n’a été passé ou si la connexion a échoué avec le nom donné, le plug-in doit inviter l’utilisateur à entrer une connexion et repasser le nom `lpUser` lorsqu’il reçoit une connexion valide. Étant donné que le plug-in peut modifier cette chaîne, l’IDE allouera toujours une mémoire tampon de taille ( `SCC_USER_LEN` + 1).

> [!NOTE]
> La première action effectuée par l’IDE peut être un appel à la `SccOpenProject` fonction ou à la `SccGetProjPath` fonction. Par conséquent, ils ont tous deux un `lpUser` paramètre identique, ce qui permet au plug-in de contrôle de code source de connecter l’utilisateur à la fois. Même si le retour de la fonction indique un échec, le plug-in doit remplir cette chaîne avec un nom de connexion valide.

 `lpLocalPath` Répertoire dans lequel l’utilisateur conserve le projet. Il peut s’agir d’une chaîne vide. Si aucun répertoire n’est actuellement défini (comme dans le cas d’un utilisateur qui tente de télécharger un projet à partir du système de contrôle de code source) et si `bAllowChangePath` est `TRUE` , le plug-in de contrôle de code source peut inviter l’utilisateur à entrer des données ou utiliser une autre méthode pour placer sa propre chaîne dans `lpLocalPath` . Si `bAllowChangePath` a `FALSE` la valeur, le plug-in ne doit pas modifier la chaîne, car l’utilisateur travaille déjà dans le répertoire spécifié.

 Si l’utilisateur crée un projet à placer sous le contrôle de code source, le plug-in de contrôle de code source peut ne pas le créer réellement dans le système de contrôle de code source au moment où `SccGetProjPath` est appelé. Au lieu de cela, elle transmet la chaîne avec une valeur différente de zéro pour `pbNew` , indiquant que le projet sera créé dans le système de contrôle de code source.

 Par exemple, si un utilisateur de l’Assistant **nouveau projet** dans Visual Studio ajoute son projet au contrôle de code source, Visual Studio appelle cette fonction et le plug-in détermine s’il est possible de créer un nouveau projet dans le système de contrôle de code source pour contenir le projet Visual Studio. Si l’utilisateur clique sur **Annuler** avant de terminer l’Assistant, le projet n’est jamais créé. Si l’utilisateur clique sur **OK**, Visual Studio appelle `SccOpenProject` , passe `SCC_OPT_CREATEIFNEW` , et le projet contrôlé par la source est créé à ce moment-là.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
