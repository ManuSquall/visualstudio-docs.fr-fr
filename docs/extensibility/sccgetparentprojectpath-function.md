---
description: Cette fonction détermine le chemin d’accès au projet parent d’un projet spécifié.
title: SccGetParentProjectPath fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900133"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath fonction)
Cette fonction détermine le chemin d’accès au projet parent d’un projet spécifié. Cette fonction est appelée lorsque l’utilisateur ajoute un projet Visual Studio au contrôle de code source.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris la marque de fin NULL).

 lpProjPath

dans Chaîne identifiant le chemin d’accès au projet (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpAuxProjPath

[in, out] Chaîne auxiliaire identifiant le projet (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpParentProjPath

[in, out] Chaîne de sortie identifiant le chemin d’accès au projet parent (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le chemin d’accès au projet parent a été obtenu avec succès.|
|SCC_E_INITIALIZEFAILED|Impossible d’initialiser le projet.|
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter au plug-in de contrôle de code source.|
|SCC_E_UNKNOWNPROJECT|Le projet est inconnu du plug-in de contrôle de code source.|
|SCC_E_INVALIDFILEPATH|Chemin de fichier non valide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|
|SCC_E_CONNECTIONFAILURE|Problème de connexion au magasin.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Cette fonction retourne un code de réussite ou d’échec et, en cas de réussite, remplit la variable `lpParentProjPath` avec le chemin d’accès complet au projet spécifié.

 Cette fonction retourne le chemin d’accès au projet parent d’un projet existant. Pour le projet racine, la fonction retourne le chemin d’accès du projet qui a été passé (autrement dit, le même chemin d’accès au projet racine). Notez qu’un chemin d’accès de projet est une chaîne qui est significative uniquement pour le plug-in de contrôle de code source.

 L’IDE est prêt à accepter également les modifications apportées aux `lpUser` `lpAuxProjPath` paramètres et. L’IDE conserve ces chaînes et les transmet au [SccOpenProject](../extensibility/sccopenproject-function.md) quand l’utilisateur ouvre ce projet à l’avenir. Ces chaînes, par conséquent, permettent au plug-in de contrôle de code source de suivre les informations qu’il doit associer à un projet.

 Cette fonction est similaire à [SccGetProjPath](../extensibility/sccgetprojpath-function.md), à ceci près qu’elle ne demande pas à l’utilisateur de sélectionner un projet. Il ne crée pas non plus un nouveau projet, mais fonctionne uniquement avec un projet existant.

 Lorsque `SccGetParentProjectPath` est appelé, `lpProjPath` et ne sont `lpAuxProjPath` pas vides et correspondent à un projet valide. Ces chaînes sont généralement reçues par l’IDE à partir d’un appel précédent à la `SccGetProjPath` fonction.

 L' `lpUser` argument est le nom d’utilisateur. L’IDE passe le même nom d’utilisateur qu’il a reçu précédemment de la `SccGetProjPath` fonction, et le plug-in de contrôle de code source doit utiliser le nom comme valeur par défaut. Si l’utilisateur dispose déjà d’une connexion ouverte avec le plug-in, le plug-in doit essayer d’éliminer les invites pour s’assurer que la fonction fonctionne en mode silencieux. Toutefois, si la connexion échoue, le plug-in doit inviter l’utilisateur à entrer une connexion et, lorsqu’il reçoit un compte de connexion valide, repasser le nom en retour `lpUser` . Étant donné que le plug-in peut modifier cette chaîne, l’IDE allouera toujours une mémoire tampon de taille ( `SCC_USER_LEN` + 1). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins aussi valide que l’ancienne chaîne).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath
 L’ajout de solutions et de projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où un utilisateur est invité à sélectionner des emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio si un plug-in de contrôle de code source prend en charge les nouvelles fonctions, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) et la `SccGetParentProjectPath` fonction. Toutefois, l’entrée de Registre suivante peut être utilisée pour désactiver ces modifications et rétablir le comportement précédent de Visual Studio (API de plug-in de contrôle de code source version 1,1) :

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword : 00000001**

 Si cette entrée de Registre n’existe pas ou est définie sur DWORD : 00000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath` .

 Si l’entrée de Registre est définie sur DWORD : 00000001, Visual Studio n’essaie pas d’utiliser ces nouvelles fonctions et les opérations d’ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
