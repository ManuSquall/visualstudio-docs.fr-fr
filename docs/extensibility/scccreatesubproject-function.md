---
title: Fonction SccCreateSubProject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701038"
---
# <a name="scccreatesubproject-function"></a>Fonction SccCreateSubProject
Cette fonction crée un sous-projet avec le nom donné `lpParentProjPath` dans le cadre d’un projet parent existant spécifié par l’argument.

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

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[dans, dehors] Le nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris le terminateur NULL).

 lpParentProjPath

[dans] Une chaîne identifiant le chemin du projet parent (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpSubProjName

[dans] Le nom sous-projet suggéré (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpAuxProjPath

[dans, dehors] Chaîne auxiliaire identifiant le projet (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

 lpSubProjPath

[dans, dehors] Chaîne de sortie identifiant le chemin du sous-projet (jusqu’à SCC_PRJPATH_SIZE, y compris le terminateur NULL).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le sous-projet a été créé avec succès.|
|SCC_E_INITIALIZEFAILED|Le projet parent n’a pas pu être parasité.|
|SCC_E_INVALIDUSER|L’utilisateur ne pouvait pas se connecter au système de contrôle source.|
|SCC_E_COULDNOTCREATEPROJECT|Le sous-projet ne peut pas être créé.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet invalide.|
|SCC_E_UNKNOWNPROJECT|Le projet parent est inconnu du plug-in de contrôle source.|
|SCC_E_INVALIDFILEPATH|Voie de fichier invalide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_CONNECTIONFAILURE|Il y avait un problème de connexion plug-in de contrôle de source.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Si un sous-projet avec le nom existe déjà, la fonction peut modifier le nom\<par défaut pour créer un nom unique, par exemple en y ajoutant « numéro> » à celui-ci. L’appelant doit être prêt `lpUser`à `lpSubProjPath`accepter `lpAuxProjPath`des changements à , , et . Les `lpSubProjPath` `lpAuxProjPath` arguments et les arguments sont ensuite utilisés dans un appel au [SccOpenProject](../extensibility/sccopenproject-function.md). Ils ne doivent pas être modifiés par l’appelant à son retour. Ces chaînes permettent au plug-in de contrôle source de suivre les informations qu’il doit associer à un projet. L’appelant IDE n’affichera pas ces deux paramètres au retour, car le plug-in peut utiliser une chaîne formatée qui pourrait ne pas convenir à la visualisation. La fonction retourne un code de réussite ou d’échec et, en cas de succès, remplit la variable `lpSubProjPath` avec le chemin complet du projet vers le nouveau projet.

 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu’elle crée silencieusement un projet plutôt que d’inciter l’utilisateur à en sélectionner un. Lorsque `SccCreateSubProject` la fonction `lpParentProjName` est `lpAuxProjPath` appelée, et ne sera pas vide et correspond à un projet valide. Ces chaînes sont généralement reçues par l’IDE `SccGetProjPath` d’un appel précédent à la fonction ou le [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 L’argument `lpUser` est le nom d’utilisateur. L’IDE passera dans le même nom d’utilisateur qu’il avait précédemment reçu de `SccGetProjPath`, et le plug-in de contrôle source devrait utiliser le nom comme un défaut. Si l’utilisateur a déjà une connexion ouverte avec le plug-in, alors le plug-in devrait essayer d’éliminer toutes les invites pour s’assurer que la fonction fonctionne silencieusement. Toutefois, si la connexion échoue, le plug-in doit inciter l’utilisateur à se connecter et, lorsqu’il reçoit une connexion valide, transmettre le nom. `lpUser` Étant donné que le plug-in peut changer cette chaîne, l’IDE allouera toujours un tampon de taille (SCC_USER_LEN 1 ou SCC_USER_SIZE, qui comprend de l’espace pour le terminateur nul). Si la corde est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins aussi valable que l’ancienne chaîne).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath
 L’ajout de solutions et de projets au contrôle des sources a été simplifié dans Visual Studio afin de minimiser le nombre de fois où un utilisateur est invité à sélectionner des emplacements dans le système de contrôle source. Ces changements sont activés par Visual Studio si un plug-in `SccCreateSubProject` `SccGetParentProjectPath`de contrôle source prend en charge les deux nouvelles fonctions, et . Cependant, l’entrée de registre suivante peut être utilisée pour désactiver ces modifications et revenir à l’ancien Visual Studio (Source Control Plug-in API Version 1.1) comportement:

 **[HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"-dword:000000001**

 Si cette entrée de registre n’existe pas ou est configuré à dword:0000000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`.

 Si l’inscription au registre est définie à dword:00000001, Visual Studio ne tente pas d’utiliser ces nouvelles fonctions, et les opérations d’ajout au travail de contrôle des sources comme ils l’ont fait dans les versions antérieures de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
