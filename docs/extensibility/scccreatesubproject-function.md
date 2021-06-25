---
description: Cette fonction crée un sous-projet portant le nom donné sous un projet parent existant spécifié par l’argument lpParentProjPath.
title: SccCreateSubProject fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6df7a801d282113b530f24472419a9735256702
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904680"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject fonction)
Cette fonction crée un sous-projet portant le nom donné sous un projet parent existant spécifié par l' `lpParentProjPath` argument.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Paramètres
 pContext

dans Pointeur de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris la marque de fin NULL).

 lpParentProjPath

dans Chaîne identifiant le chemin d’accès du projet parent (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpSubProjName

dans Nom de sous-projet suggéré (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpAuxProjPath

[in, out] Chaîne auxiliaire identifiant le projet (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

 lpSubProjPath

[in, out] Chaîne de sortie identifiant le chemin d’accès du sous-projet (jusqu’à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le sous-projet a été créé avec succès.|
|SCC_E_INITIALIZEFAILED|Impossible d’initialiser le projet parent.|
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter au système de contrôle de code source.|
|SCC_E_COULDNOTCREATEPROJECT|Impossible de créer un sous-projet.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|
|SCC_E_UNKNOWNPROJECT|Le projet parent est inconnu du plug-in de contrôle de code source.|
|SCC_E_INVALIDFILEPATH|Chemin de fichier non valide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_CONNECTIONFAILURE|Un problème est survenu lors de la connexion du plug-in de contrôle de code source.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Si un sous-projet portant le même nom existe déjà, la fonction peut modifier le nom par défaut pour en créer un unique, par exemple en lui ajoutant « _ \<number> ». L’appelant doit être prêt à accepter les modifications apportées à `lpUser` , `lpSubProjPath` et `lpAuxProjPath` . Les `lpSubProjPath` `lpAuxProjPath` arguments et sont ensuite utilisés dans un appel à [SccOpenProject](../extensibility/sccopenproject-function.md). Elles ne doivent pas être modifiées par l’appelant lors du retour. Ces chaînes permettent au plug-in de contrôle de code source de suivre les informations qu’il doit associer à un projet. L’IDE de l’appelant n’affichera pas ces deux paramètres lors du retour, car le plug-in peut utiliser une chaîne mise en forme qui peut ne pas convenir à l’affichage. La fonction retourne un code de réussite ou d’échec et, en cas de réussite, remplit la variable `lpSubProjPath` avec le chemin d’accès complet du projet au nouveau projet.

 Cette fonction est similaire à [SccGetProjPath](../extensibility/sccgetprojpath-function.md), à ceci près qu’elle crée un projet en mode silencieux plutôt que d’inviter l’utilisateur à en sélectionner une. Lorsque la `SccCreateSubProject` fonction est appelée, `lpParentProjName` et ne sont `lpAuxProjPath` pas vides et correspondent à un projet valide. Ces chaînes sont généralement reçues par l’IDE à partir d’un appel précédent à la `SccGetProjPath` fonction ou à [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 L' `lpUser` argument est le nom d’utilisateur. L’IDE passe le même nom d’utilisateur qu’à partir duquel il a reçu précédemment `SccGetProjPath` , et le plug-in de contrôle de code source doit utiliser le nom comme valeur par défaut. Si l’utilisateur dispose déjà d’une connexion ouverte avec le plug-in, le plug-in doit essayer d’éliminer les invites pour s’assurer que la fonction fonctionne en mode silencieux. Toutefois, si la connexion échoue, le plug-in doit inviter l’utilisateur à entrer une connexion et, lorsqu’il reçoit un compte de connexion valide, repasser le nom en retour `lpUser` . Étant donné que le plug-in peut modifier cette chaîne, l’IDE allouera toujours une mémoire tampon de taille (SCC_USER_LEN + 1 ou SCC_USER_SIZE, qui comprend de l’espace pour la marque de fin null). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins aussi valide que l’ancienne chaîne).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath
 L’ajout de solutions et de projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où un utilisateur est invité à sélectionner des emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio si un plug-in de contrôle de code source prend en charge les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath` . Toutefois, l’entrée de Registre suivante peut être utilisée pour désactiver ces modifications et rétablir le comportement précédent de Visual Studio (API de plug-in de contrôle de code source version 1,1) :

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword : 00000001**

 Si cette entrée de Registre n’existe pas ou est définie sur DWORD : 00000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath` .

 Si l’entrée de Registre est définie sur DWORD : 00000001, Visual Studio n’essaie pas d’utiliser ces nouvelles fonctions et les opérations d’ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
