---
title: SccOpenProject fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721053"
---
# <a name="sccopenproject-function"></a>Fonction SccOpenProject
Cette fonction ouvre un projet de contrôle de code source existant ou en crée un.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[in, out] Nom de l’utilisateur (à ne pas dépasser SCC_USER_SIZE, y compris la marque de fin NULL).

 lpProjName

dans Chaîne identifiant le nom du projet.

 lpLocalProjPath

dans Chemin d’accès au dossier de travail pour le projet.

 lpAuxProjPath

[in, out] Chaîne auxiliaire facultative identifiant le projet (sans dépasser SCC_AUXPATH_SIZE, y compris la marque de fin NULL).

 lpComment

dans Commentez un nouveau projet en cours de création.

 lpTextOutProc

dans Fonction de rappel facultative permettant d’afficher la sortie de texte à partir du plug-in de contrôle de code source.

 dwFlags

dans Signale si un nouveau projet doit être créé si le projet est inconnu du plug-in de contrôle de code source. La valeur peut être une combinaison de `SCC_OP_CREATEIFNEW` et `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite de l’ouverture du projet.|
|SCC_E_INITIALIZEFAILED|Impossible d’initialiser le projet.|
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter au système de contrôle de code source.|
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’existait pas avant l’appel ;  l’indicateur de `SCC_OPT_CREATEIFNEW` a été défini, mais le projet n’a pas pu être créé.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|
|SCC_E_UNKNOWNPROJECT|Le projet est inconnu du plug-in de contrôle de code source et l’indicateur `SCC_OPT_CREATEIFNEW` n’a pas été défini.|
|SCC_E_INVALIDFILEPATH|Chemin de fichier non valide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECFICERROR|Une défaillance non spécifique ; le système de contrôle de code source n’a pas été initialisé.|

## <a name="remarks"></a>Notes
 L’IDE peut passer un nom d’utilisateur (`lpUser`) ou il peut simplement passer un pointeur vers une chaîne vide. S’il existe un nom d’utilisateur, le plug-in de contrôle de code source doit l’utiliser comme valeur par défaut. Toutefois, si aucun nom n’a été passé, ou si la connexion a échoué avec le nom donné, le plug-in doit inviter l’utilisateur à se connecter et renverra le nom valide dans `lpUser` lorsqu’il reçoit une connexion valide `.` car le plug-in peut modifier la chaîne de nom d’utilisateur , l’IDE allouera toujours une mémoire tampon de taille (`SCC_USER_LEN` + 1 ou SCC_USER_SIZE, qui comprend l’espace pour la marque de fin null).

> [!NOTE]
> La première action que l’IDE peut être amené à effectuer peut être un appel à la fonction `SccOpenProject` ou à [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Pour cette raison, les deux ont un paramètre `lpUser` identique.

 `lpAuxProjPath` et `lpProjName` sont lus à partir du fichier solution, ou ils sont retournés à partir d’un appel à la fonction `SccGetProjPath`. Ces paramètres contiennent les chaînes que le plug-in de contrôle de code source associe au projet et qui sont significatives uniquement pour le plug-in. Si aucune chaîne de ce type n’est présente dans le fichier solution et que l’utilisateur n’a pas été invité à parcourir (ce qui retournerait une chaîne via la fonction `SccGetProjPath`), l’IDE passe des chaînes vides pour `lpAuxProjPath` et `lpProjName`, et s’attend à ce que ces valeurs soient mises à jour par le plug-in lorsque th est retourné par la fonction.

 `lpTextOutProc` est un pointeur vers une fonction de rappel fournie par l’IDE au plug-in de contrôle de code source pour l’affichage de la sortie des résultats de la commande. Cette fonction de rappel est décrite en détail dans [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si le plug-in de contrôle de code source a l’intention de tirer parti de cela, il doit avoir défini l’indicateur `SCC_CAP_TEXTOUT` dans le [SccInitialize](../extensibility/sccinitialize-function.md). Si cet indicateur n’a pas été défini, ou si l’IDE ne prend pas en charge cette fonctionnalité, `lpTextOutProc` sera `NULL`.

 Le paramètre `dwFlags` contrôle le résultat dans le cas où le projet en cours d’ouverture n’existe pas actuellement. Il se compose de deux indicateurs, `SCC_OP_CREATEIFNEW` et `SCC_OP_SILENTOPEN`. Si le projet ouvert existe déjà, la fonction ouvre simplement le projet et retourne `SCC_OK`. Si le projet n’existe pas et si l’indicateur `SCC_OP_CREATEIFNEW` est activé, le plug-in de contrôle de code source peut créer le projet dans le système de contrôle de code source, l’ouvrir et retourner `SCC_OK`. Si le projet n’existe pas et si l’indicateur de `SCC_OP_CREATEIFNEW` est désactivé, le plug-in doit ensuite Rechercher l’indicateur de `SCC_OP_SILENTOPEN`. Si cet indicateur n’est pas activé, le plug-in peut inviter l’utilisateur à entrer un nom de projet. Si cet indicateur est activé, le plug-in doit simplement retourner `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Ordre d’appel
 Dans le cadre normal des événements, le [SccInitialize](../extensibility/sccinitialize-function.md) est appelé en premier pour ouvrir une session de contrôle de code source. Une session peut se composer d’un appel à `SccOpenProject`, suivi d’autres appels de fonction d’API du plug-in de contrôle de code source et se termine par un appel à [SccCloseProject](../extensibility/scccloseproject-function.md). De telles sessions peuvent être répétées plusieurs fois avant l’appel de [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Si le plug-in de contrôle de code source définit le bit de `SCC_CAP_REENTRANT` dans `SccInitialize`, la séquence de session ci-dessus peut être répétée plusieurs fois en parallèle. Les différentes structures de `pvContext` effectuent le suivi des différentes sessions, dans lesquelles chaque `pvContext` est associé à un projet ouvert à la fois. En fonction du paramètre `pvContext`, le plug-in peut déterminer quel projet est référencé dans un appel particulier. Si le bit de fonctionnalité `SCC_CAP_REENTRANT` n’est pas défini, les plug-ins de contrôle de code source nonreentrant sont limités dans leur capacité à travailler avec plusieurs projets.

> [!NOTE]
> Le bit de `SCC_CAP_REENTRANT` a été introduit dans la version 1,1 de l’API de plug-in de contrôle de code source. Elle n’est pas définie ou est ignorée dans la version 1,0, et tous les plug-ins de contrôle de code source version 1,0 sont supposés être nonreentrant.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restrictions relatives aux longueurs de chaînes](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)