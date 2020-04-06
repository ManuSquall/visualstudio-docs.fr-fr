---
title: Fonction SccOpenProject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700565"
---
# <a name="sccopenproject-function"></a>Fonction SccOpenProject
Cette fonction ouvre un projet de contrôle source existant ou en crée un nouveau.

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
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpUser

[dans, dehors] Le nom de l’utilisateur (ne pas dépasser SCC_USER_SIZE, y compris le terminateur NULL).

 lpProjName

[dans] La chaîne identifiant le nom du projet.

 lpLocalProjPath (en)

[dans] Le chemin vers le dossier de travail pour le projet.

 lpAuxProjPath

[dans, dehors] Une chaîne auxiliaire facultative identifiant le projet (ne pas dépasser SCC_AUXPATH_SIZE, y compris le terminateur NULL).

 lpComment

[dans] Commentaire à un nouveau projet qui est en cours de création.

 lpTextOutProc

[dans] Une fonction de rappel optionnelle pour afficher la sortie de texte à partir du plug-in de contrôle source.

 dwFlags

[dans] Indique si un nouveau projet doit être créé si le projet est inconnu du plug-in de contrôle source. La valeur peut `SCC_OP_CREATEIFNEW` être une combinaison de`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Succès dans l’ouverture du projet.|
|SCC_E_INITIALIZEFAILED|Le projet n’a pas pu être parasécé.|
|SCC_E_INVALIDUSER|L’utilisateur ne pouvait pas se connecter au système de contrôle source.|
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’existait pas avant l’appel;  le `SCC_OPT_CREATEIFNEW` drapeau a été fixé, mais le projet n’a pas pu être créé.|
|SCC_E_PROJSYNTAXERR|Syntaxe de projet invalide.|
|SCC_E_UNKNOWNPROJECT|Le projet est inconnu du plug-in `SCC_OPT_CREATEIFNEW` de contrôle source, et le drapeau n’a pas été fixé.|
|SCC_E_INVALIDFILEPATH|Voie de fichier invalide ou inutilisable.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECFICERROR|Un échec non spécifique; le système de contrôle à la source n’a pas été parasécisé.|

## <a name="remarks"></a>Notes
 L’IDE peut passer dans`lpUser`un nom d’utilisateur ( ), ou il peut simplement passer dans un pointeur à une chaîne vide. S’il y a un nom d’utilisateur, le plug-in de contrôle source doit l’utiliser par défaut. Toutefois, si aucun nom n’a été adopté, ou si la connexion a échoué avec le nom donné, le plug-in devrait inciter l’utilisateur à se connecter et retourner le nom valide `lpUser` quand il reçoit une connexion valide`.` Parce que le plug-in peut changer la chaîne de nom d’utilisateur, l’IDE sera toujours allouer un tampon de taille (1`SCC_USER_LEN`ou SCC_USER_SIZE, qui comprend l’espace pour le terminateur nul).

> [!NOTE]
> La première action que l’IDE peut être `SccOpenProject` tenue d’effectuer peut être un appel à la fonction ou le [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Pour cette raison, les deux `lpUser` ont un paramètre identique.

 `lpAuxProjPath`et`lpProjName` sont lus à partir du fichier de `SccGetProjPath` solution, ou ils sont retournés d’un appel à la fonction. Ces paramètres contiennent les chaînes que le plug-in de contrôle source associe au projet et ne sont significatives que pour le plug-in. Si ces chaînes ne sont pas dans le fichier de solution et que l’utilisateur n’a pas été invité à naviguer (ce qui retournerait une chaîne à travers la `SccGetProjPath` fonction), l’IDE passe les cordes vides pour les deux `lpAuxProjPath` et, `lpProjName`et s’attend à ce que ces valeurs soient mises à jour par le plug-in lorsque cette fonction revient.

 `lpTextOutProc`est un pointeur d’une fonction de rappel fournie par l’IDE au plug-in de contrôle source dans le but d’afficher la sortie du résultat de commande. Cette fonction de rappel est décrite en détail dans [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si le plug-in de contrôle source a l’intention `SCC_CAP_TEXTOUT` d’en profiter, il doit avoir placé le drapeau dans le [SccInitialize](../extensibility/sccinitialize-function.md). Si ce drapeau n’a pas été défini, ou `lpTextOutProc` si `NULL`l’IDE ne prend pas en charge cette fonctionnalité, sera .

 Le `dwFlags` paramètre contrôle le résultat dans le cas où le projet en cours d’ouverture n’existe pas actuellement. Il se compose de `SCC_OP_CREATEIFNEW` deux `SCC_OP_SILENTOPEN`bitflags, et . Si le projet en cours d’ouverture existe déjà, la fonction ouvre simplement le projet et revient. `SCC_OK` Si le projet n’existe `SCC_OP_CREATEIFNEW` pas et si le drapeau est allumé, le plug-in de contrôle `SCC_OK`source peut créer le projet dans le système de contrôle source, l’ouvrir, et le retourner . Si le projet n’existe `SCC_OP_CREATEIFNEW` pas et si le drapeau est éteint, le plug-in doit alors vérifier le `SCC_OP_SILENTOPEN` drapeau. Si ce drapeau n’est pas allumé, le plug-in peut inciter l’utilisateur à obtenir un nom de projet. Si ce drapeau est allumé, le `SCC_E_UNKNOWNPROJECT`plug-in doit simplement revenir .

## <a name="calling-order"></a>Ordre d’appel
 Dans le cours normal des événements, la [SccInitialize](../extensibility/sccinitialize-function.md) serait appelée la première à ouvrir une session de contrôle source. Une session peut consister `SccOpenProject`en un appel à , suivie par d’autres appels de fonction de contrôle source plug-in API, et se terminera par un appel à la [SccCloseProject](../extensibility/scccloseproject-function.md). De telles séances peuvent être répétées plusieurs fois avant que la [SccUninitialize ne](../extensibility/sccuninitialize-function.md) soit appelée.

 Si le plug-in de `SCC_CAP_REENTRANT` contrôle `SccInitialize`source définit le bit, alors la séquence de session ci-dessus peut être répétée plusieurs fois en parallèle. Différentes `pvContext` structures suivent les différentes `pvContext` sessions, dans lesquelles chacune est associée à un projet ouvert à la fois. Sur la`pvContext` base du paramètre, le plug-in peut déterminer quel projet est référencé dans un appel particulier. Si le `SCC_CAP_REENTRANT` bit de capacité n’est pas réglé, les plug-ins de contrôle des sources non-entrarants sont limités dans leur capacité à travailler avec plusieurs projets.

> [!NOTE]
> Le `SCC_CAP_REENTRANT` bit a été introduit dans la version 1.1 de l’API de contrôle source plug-in. Il n’est pas défini ou est ignoré dans la version 1.0, et toutes les version 1.0 plug-ins de contrôle de source sont supposés être nonentrant.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restrictions relatives aux longueurs de chaînes](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
