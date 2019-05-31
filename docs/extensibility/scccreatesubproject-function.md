---
title: Fonction SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aa70f6b42a6722ac66340807503ee4494795b0d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327524"
---
# <a name="scccreatesubproject-function"></a>Fonction SccCreateSubProject
Cette fonction crée un sous-projet portant le nom spécifié sous un projet parent existant spécifié par le `lpParentProjPath` argument.

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

[in] Le pointeur de contexte de plug-in de contrôle de code source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Le nom d’utilisateur (jusqu'à SCC_USER_SIZE, y compris le terminateur NULL).

 lpParentProjPath

[in] Chaîne identifiant le chemin d’accès du projet parent (jusqu'à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpSubProjName

[in] Le nom suggéré sous-projet (jusqu'à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpAuxProjPath

[in, out] Auxiliaire chaîne identifiant le projet (jusqu'à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpSubProjPath

[in, out] Chaîne de sortie qui identifie le chemin d’accès pour le sous-projet (jusqu'à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Sous-projet a été créé avec succès.|
|SCC_E_INITIALIZEFAILED|Projet parent n’a pas pu être initialisé.|
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter le système de contrôle source.|
|SCC_E_COULDNOTCREATEPROJECT|Impossible de créer le sous-projet.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|
|SCC_E_UNKNOWNPROJECT|Le projet parent est inconnu pour le plug-in de contrôle de code source.|
|SCC_E_INVALIDFILEPATH|Chemin d’accès de fichier non valide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_CONNECTIONFAILURE|Il a été un problème de connexion de plug-in de contrôle de code source.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|

## <a name="remarks"></a>Notes
 Si un sous-projet portant le nom existe déjà, la fonction peut modifier le nom par défaut pour créer un unique, par exemple en ajoutant « _\<nombre > » à ce dernier. L’appelant doit être prêt à accepter les modifications de `lpUser`, `lpSubProjPath`, et `lpAuxProjPath`. Le `lpSubProjPath` et`lpAuxProjPath` arguments sont ensuite utilisées dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). Ils ne doivent pas être modifiés par l’appelant lors du retour. Ces chaînes constituent un moyen pour le plug-in pour le suivi des informations dont il a besoin à associer à un projet de contrôle de code source. L’appelant IDE n’affiche pas ces deux paramètres au moment du retour, car le plug-in peut utiliser une chaîne mise en forme qui peut ne pas convenir pour l’affichage. La fonction retourne un code de réussite ou l’échec et, en cas de réussite, remplit la variable `lpSubProjPath` avec le chemin d’accès de projet complet vers le nouveau projet.

 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), à ceci près qu’il crée en mode silencieux un projet au lieu d’inviter l’utilisateur à sélectionner un. Lorsque le `SccCreateSubProject` fonction est appelée, `lpParentProjName` et `lpAuxProjPath` ne sera pas vide et correspond à un projet valid. Ces chaînes sont généralement reçus par l’IDE à partir d’un appel précédent à la `SccGetProjPath` fonction ou le [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Le `lpUser` argument est le nom d’utilisateur. L’IDE passe dans le même nom d’utilisateur qui il a précédemment reçu à partir de `SccGetProjPath`, et le plug-in de contrôle de code source doit utiliser le nom par défaut. Si l’utilisateur possède déjà une connexion ouverte avec le plug-in, le plug-in doit essayer d’éliminer les invites pour vous assurer que la fonction fonctionne en mode silencieux. Toutefois, si la connexion échoue, le plug-in doit inviter l’utilisateur pour un compte de connexion et, lorsqu’il reçoit une connexion valide, passez le nom de nouveau `lpUser`. Étant donné que le plug-in peut modifier cette chaîne, l’IDE sera toujours allouer une mémoire tampon de taille (SCC_USER_LEN + 1 ou SCC_USER_SIZE, qui inclut l’espace pour le terminateur null). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins comme étant valide en tant que l’ancienne chaîne).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath
 Ajout de solutions et projets au contrôle de code source a été simplifié dans Visual Studio pour réduire le nombre de fois où qu'un utilisateur est invité à sélectionner les emplacements dans le système de contrôle source. Ces modifications sont activées par Visual Studio si un plug-in de contrôle de code source prend en charge des nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`. Toutefois, l’entrée de Registre suivante peut être utilisée pour désactiver ces modifications et revenir au comportement précédent de Visual Studio (Source contrôle plug-in API Version 1.1) :

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Si cette entrée de Registre n’existe pas ou a la valeur DWORD : 00000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`.

 Si l’entrée de Registre est définie sur DWORD : 00000001, Visual Studio n’essaie pas d’utiliser ces nouvelles fonctions et les opérations d’ajout au contrôle de code source fonctionnent comme ils le faisaient dans les versions antérieures de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)