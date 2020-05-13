---
title: Fonction SccGetParentProjectPath (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700717"
---
# <a name="sccgetparentprojectpath-function"></a>Fonction SccGetParentProjectPath
Cette fonction détermine le parcours du projet parent d’un projet spécifié. Cette fonction est appelée lorsque l’utilisateur ajoute un projet Visual Studio pour le contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[dans, dehors] Le nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris le terminateur NULL).

 lpProjPath (en)

[dans] Chaîne identifiant le chemin du projet (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpAuxProjPath

[dans, dehors] Chaîne auxiliaire identifiant le projet (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpParentProjPath

[dans, dehors] Chaîne de sortie identifiant le chemin du projet parent (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le chemin du projet parent a été obtenu avec succès.|
|SCC_E_INITIALIZEFAILED|Le projet n’a pas pu être parasécé.|
|SCC_E_INVALIDUSER|L’utilisateur ne pouvait pas se connecter au plug-in de contrôle source.|
|SCC_E_UNKNOWNPROJECT|Le projet est inconnu du plug-in de contrôle source.|
|SCC_E_INVALIDFILEPATH|Voie de fichier invalide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet invalide.|
|SCC_E_CONNECTIONFAILURE|Problème de connexion de magasin.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction renvoie un code de réussite ou `lpParentProjPath` d’échec et, en cas de succès, remplit la variable avec le chemin complet du projet vers le projet spécifié.

 Cette fonction renvoie la trajectoire du projet parent d’un projet existant. Pour le projet racine, la fonction retourne le chemin du projet qui a été transmis (c’est-à-dire, le même chemin de projet racine). Notez qu’un chemin de projet est une chaîne qui n’a de sens qu’au plug-in de contrôle source.

 L’IDE est prêt à `lpUser` `lpAuxProjPath` accepter les modifications apportées aux paramètres et aux paramètres. L’IDE persistera ces chaînes et les passera au [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque l’utilisateur ouvrira ce projet à l’avenir. Ces chaînes constituent donc un moyen pour le plug-in de contrôle source de suivre les informations dont il a besoin pour s’associer à un projet.

 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu’elle n’incite pas l’utilisateur à sélectionner un projet. Il ne crée jamais non plus de nouveau projet, mais ne fonctionne qu’avec un projet existant.

 Quand `SccGetParentProjectPath` est `lpProjPath` appelé, et `lpAuxProjPath` ne sera pas vide et correspondra à un projet valide. Ces chaînes sont généralement reçues par l’IDE `SccGetProjPath` d’un appel précédent à la fonction.

 L’argument `lpUser` est le nom d’utilisateur. L’IDE passera dans le même nom d’utilisateur `SccGetProjPath` qu’il avait précédemment reçu de la fonction, et le plug-in de contrôle source devrait utiliser le nom comme un défaut. Si l’utilisateur a déjà une connexion ouverte avec le plug-in, alors le plug-in devrait essayer d’éliminer toutes les invites pour s’assurer que la fonction fonctionne silencieusement. Toutefois, si la connexion échoue, le plug-in doit inciter l’utilisateur à se connecter et, lorsqu’il reçoit une connexion valide, transmettre le nom. `lpUser` Étant donné que le plug-in peut modifier cette chaîne, l’IDE allouera toujours un tampon de taille (no`SCC_USER_LEN`1). Si la corde est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins aussi valable que l’ancienne chaîne).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath
 L’ajout de solutions et de projets au contrôle des sources a été simplifié dans Visual Studio afin de minimiser le nombre de fois où un utilisateur est invité à sélectionner des emplacements dans le système de contrôle source. Ces modifications sont activées par Visual Studio si un plug-in de contrôle source prend en `SccGetParentProjectPath` charge à la fois les nouvelles fonctions, le [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) et la fonction. Cependant, l’entrée de registre suivante peut être utilisée pour désactiver ces modifications et revenir au comportement précédent de Visual Studio (Source Control Plug-in API Version 1.1) :

 **[HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"-dword:000000001**

 Si cette entrée de registre n’existe pas ou est configuré à dword:0000000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject`et`SccGetParentProjectPath`.

 Si l’inscription au registre est définie à dword:00000001, Visual Studio ne tente pas d’utiliser ces nouvelles fonctions, et les opérations d’ajout au travail de contrôle des sources comme ils l’ont fait dans les versions antérieures de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
