---
title: Fonction SccGetProjPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053d8ff8f7e75224b05b1a722ba1bce03cd53a59
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948438"
---
# <a name="sccgetprojpath-function"></a>Fonction SccGetProjPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction invite l’utilisateur à un chemin d’accès du projet, qui est une chaîne qui est uniquement explicite pour le plug-in de contrôle de code source. Elle est appelée lorsque l’utilisateur est :  
  
-   Création d’un projet  
  
-   Ajouter un projet existant au contrôle de version  
  
-   Une tentative de recherche d’un projet de contrôle de version existant  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [in, out] Le nom d’utilisateur (ne dépassant pas SCC_USER_SIZE, y compris le terminateur NULL)  
  
 lpProjName  
 [in, out] Le nom de l’IDE projet, espace de travail de projet ou makefile (ne dépassant pas SCC_PRJPATH_SIZE, y compris le terminateur NULL).  
  
 lpLocalPath  
 [in, out] Chemin d’accès de travail du projet. Si `bAllowChangePath` est `TRUE`, le plug-in de contrôle de code source peut modifier cette chaîne (ne dépassant pas _MAX_PATH, y compris la marque de fin null).  
  
 lpAuxProjPath  
 [in, out] Une mémoire tampon pour le chemin d’accès de projet retourné (ne dépassant pas SCC_PRJPATH_SIZE, y compris le terminateur NULL).  
  
 bAllowChangePath  
 [in] S’il s’agit `TRUE`, le plug-in de contrôle de code source peut demander et modifier le `lpLocalPath` chaîne.  
  
 pbNew  
 [in, out] Valeur bientôt indique s’il faut créer un nouveau projet. Valeur retournée indique la réussite de la création d’un projet :  
  
|Entrant|Interprétation|  
|--------------|--------------------|  
|true|L’utilisateur peut créer un nouveau projet.|  
|false|L’utilisateur ne peut pas créer un nouveau projet.|  
  
|Sortant|Interprétation|  
|--------------|--------------------|  
|true|Un nouveau projet a été créé.|  
|false|Un projet existant a été sélectionné.|  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le projet a été correctement créé ou récupéré.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_CONNECTIONFAILURE|Un tentative de connexion au système de contrôle de source de problème est survenu.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|  
  
## <a name="remarks"></a>Notes  
 L’objectif de cette fonction est pour l’IDE acquérir les paramètres `lpProjName` et `lpAuxProjPath`. Une fois que le plug-in de contrôle de code source invite l’utilisateur pour obtenir ces informations, il transmet ces deux chaînes à l’IDE. L’IDE persiste ces chaînes dans son fichier de solution et les transmet à la [SccOpenProject](../extensibility/sccopenproject-function.md) chaque fois que l’utilisateur ouvre ce projet. Ces chaînes activer le plug-in effectuer le suivi des informations associées à un projet.  
  
 Lorsque la fonction est appelée tout d’abord, `lpAuxProjPath` est définie sur une chaîne vide. `lProjName` peut également être vide, ou il peut contenir le nom du projet IDE, ce qui le plug-in de contrôle de code source peut utiliser ou ignorer. Lorsque la fonction est retournée avec succès, le plug-in renvoie les deux chaînes correspondants. L’IDE n’émet aucune hypothèse sur ces chaînes ne les utiliserez pas et n’autorise pas l’utilisateur de les modifier. Si l’utilisateur souhaite modifier les paramètres, l’IDE appellera `SccGetProjPath` à nouveau, en passant les mêmes valeurs qu’il a reçu l’heure précédente. Ainsi, le plug-in contrôle complet sur ces deux chaînes.  
  
 Pour `lpUser`, l’IDE peut transmettre un nom d’utilisateur, ou il peut simplement passer un pointeur vers une chaîne vide. S’il existe un nom d’utilisateur, le plug-in de contrôle de code source doit l’utiliser comme valeur par défaut. Toutefois, si aucun nom n’a été passée ou si la connexion a échoué avec le nom donné, le plug-in doit inviter l’utilisateur pour une connexion et la passe de nouveau le nom `lpUser` lorsqu’elle reçoit une connexion valide. Étant donné que le plug-in peut modifier cette chaîne, l’IDE sera toujours allouer une mémoire tampon de taille (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  La première action qui effectue l’IDE peut être un appel à la `SccOpenProject` fonction ou le `SccGetProjPath` (fonction). Par conséquent, deux d'entre eux ont un identiques `lpUser` paramètre, ce qui permet le plug-in pour connecter l’utilisateur au moment du contrôle de code source. Même si le retour à partir de la fonction indique un échec, le plug-in doit remplir cette chaîne avec un nom de connexion valide.  
  
 `lpLocalPath` est le répertoire où l’utilisateur maintient le projet. Il peut être une chaîne vide. Si aucun répertoire actuellement définies (comme dans le cas d’un utilisateur tente de télécharger un projet à partir du système de contrôle de source) et si `bAllowChangePath` est `TRUE`, le plug-in de contrôle de code source peut inviter l’utilisateur pour l’entrée ou utilisez une autre méthode pour placer ses propriétaire de chaîne dans `lpLocalPath`. Si `bAllowChangePath` est `FALSE`, le plug-in ne devez pas modifier la chaîne, étant donné que l’utilisateur travaille déjà dans le répertoire spécifié.  
  
 Si l’utilisateur crée un nouveau projet à placer sous contrôle de code source, le plug-in de contrôle de code source ne peut pas réellement créer dans le système de contrôle de source au moment `SccGetProjPath` est appelée. Au lieu de cela, il passe à nouveau la chaîne avec une valeur différente de zéro pour `pbNew`, indiquant que le projet sera créé dans le système de contrôle de code source.  
  
 Par exemple, si un utilisateur dans le **nouveau projet** Assistant dans Visual Studio ajoute son propre projet au contrôle de code source, Visual Studio appelle cette fonction, et détermine le plug-in si elle est OK créer un nouveau projet dans le système de contrôle de source pour contient le projet de Visual Studio. Si l’utilisateur clique sur **Annuler** avant la fin de l’Assistant, le projet n’est jamais créé. Si l’utilisateur clique sur **OK**, Visual Studio appelle `SccOpenProject`, en passant dans `SCC_OPT_CREATEIFNEW`, et le projet de contrôle de code source est créé à ce moment-là.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
