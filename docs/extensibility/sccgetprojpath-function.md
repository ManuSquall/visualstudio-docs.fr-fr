---
title: Fonction de SccGetProjPath | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 551fe26fe20da62d6892a8c7e807cf6c22600fc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (fonction)
Cette fonction invite l’utilisateur à un chemin d’accès du projet, qui est une chaîne qui est uniquement explicite pour le plug-in de contrôle de code source. Elle est appelée lorsque l’utilisateur est :  
  
-   Création d’un projet  
  
-   Ajouter un projet existant au contrôle de version  
  
-   Tentative de recherche d’un projet de contrôle de version existant  
  
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
 [in] La structure de contexte du plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [dans, out] Le nom d’utilisateur (à ne pas dépasser SCC_USER_SIZE, y compris le terminateur NULL)  
  
 lpProjName  
 [dans, out] Le nom du projet IDE, espace de travail project ou makefile (à ne pas dépasser SCC_PRJPATH_SIZE, y compris le terminateur NULL).  
  
 lpLocalPath  
 [dans, out] Chemin d’accès de travail du projet. Si `bAllowChangePath` est `TRUE`, le plug-in de contrôle de code source peut modifier cette chaîne (ne dépassant pas _MAX_PATH, y compris la marque de fin null).  
  
 lpAuxProjPath  
 [dans, out] Une mémoire tampon pour le chemin d’accès de projet retourné (à ne pas dépasser SCC_PRJPATH_SIZE, y compris le terminateur NULL).  
  
 bAllowChangePath  
 [in] S’il s’agit `TRUE`, le plug-in de contrôle de code source peut demander et modifier le `lpLocalPath` chaîne.  
  
 pbNew  
 [dans, out] Valeur d’indique s’il faut créer un nouveau projet. Valeur retournée indique la réussite de la création d’un projet :  
  
|Entrant|Interprétation|  
|--------------|--------------------|  
|TRUE|L’utilisateur peut créer un nouveau projet.|  
|FALSE|L’utilisateur ne peut pas créer un nouveau projet.|  
  
|Sortant|Interprétation|  
|--------------|--------------------|  
|TRUE|Un nouveau projet a été créé.|  
|FALSE|Un projet existant a été sélectionné.|  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le projet a été correctement créé ou récupéré.|  
|SCC_I_OPERATIONCANCELED|L'opération a été annulée.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_CONNECTIONFAILURE|Il a été un problème, essayez de vous connecter au système de contrôle source.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|  
  
## <a name="remarks"></a>Remarques  
 L’objectif de cette fonction est l’IDE acquérir les paramètres `lpProjName` et `lpAuxProjPath`. Une fois que le plug-in de contrôle de code source invite l’utilisateur pour obtenir cette information, il transmet ces deux chaînes à l’IDE. L’IDE persiste ces chaînes dans son fichier de solution et les transmet à la [SccOpenProject](../extensibility/sccopenproject-function.md) chaque fois que l’utilisateur ouvre ce projet. Ces chaînes activer le plug-in pour le suivi des informations associées à un projet.  
  
 Lorsque la fonction est appelée tout d’abord, `lpAuxProjPath` est définie sur une chaîne vide. `lProjName`peut également être vide, ou il peut contenir le nom du projet IDE, ce qui le plug-in de contrôle de code source peut utiliser ou ignorer. Lorsque la fonction est retournée avec succès, le plug-in renvoie les deux chaînes correspondantes. L’IDE n’émet aucune hypothèse sur ces chaînes ne les utiliserez pas et n’autorise pas l’utilisateur de les modifier. Si l’utilisateur souhaite modifier les paramètres, l’IDE appelle `SccGetProjPath` , en passant les mêmes valeurs qu’il a reçu la dernière fois. Ainsi, le plug-in contrôle complet sur ces deux chaînes.  
  
 Pour `lpUser`, l’IDE peut transmettre un nom d’utilisateur, ou il peut simplement passer un pointeur vers une chaîne vide. S’il existe un nom d’utilisateur, le plug-in de contrôle de code source doit l’utiliser comme valeur par défaut. Toutefois, si aucun nom n’a été passée ou si la connexion a échoué avec le nom donné, le plug-in doit inviter l’utilisateur pour une connexion et la passe de nouveau le nom `lpUser` lorsqu’elle reçoit une connexion valide. Étant donné que le plug-in peut modifier cette chaîne, l’IDE sera toujours allouer un tampon de taille (`SCC_USER_LEN`+&1;).  
  
> [!NOTE]
>  La première action que l’IDE effectue peut être un appel à la `SccOpenProject` (fonction) ou `SccGetProjPath` (fonction). Par conséquent, deux d'entre eux ont un identiques `lpUser` paramètre, ce qui permet le plug-in pour connecter l’utilisateur au moment du contrôle de code source. Même si le retour de la fonction indique un échec, le plug-in doit remplir cette chaîne avec un nom de connexion valide.  
  
 `lpLocalPath`est le répertoire où l’utilisateur conserve le projet. Il peut être une chaîne vide. Si aucun répertoire actuellement définies (comme dans le cas d’un utilisateur tente de télécharger un projet à partir du système de contrôle source) et si `bAllowChangePath` est `TRUE`, le plug-in de contrôle de code source peut inviter l’utilisateur à entrer ou utiliser une autre méthode pour placer sa propre chaîne dans `lpLocalPath`. Si `bAllowChangePath` est `FALSE`, le plug-in ne devez pas modifier la chaîne, étant donné que l’utilisateur travaille déjà dans le répertoire spécifié.  
  
 Si l’utilisateur crée un nouveau projet à placer sous contrôle de code source, le plug-in de contrôle de code source ne peut pas réellement créer dans le système de contrôle de code source au moment `SccGetProjPath` est appelée. Au lieu de cela, il passe à nouveau la chaîne avec une valeur différente de zéro pour `pbNew`, indiquant que le projet sera créé dans le système de contrôle de code source.  
  
 Par exemple, si un utilisateur de la **nouveau projet** Assistant dans Visual Studio ajoute son propre projet au contrôle de code source, Visual Studio appelle cette fonction et le plug-in détermine s’il est OK créer un nouveau projet dans le système de contrôle de code source pour contenir le projet Visual Studio. Si l’utilisateur clique sur **Annuler** avant la fin de l’Assistant, le projet n’est pas créé. Si l’utilisateur clique sur **OK**, Visual Studio appelle `SccOpenProject`, en passant dans `SCC_OPT_CREATEIFNEW`, et le projet de contrôle de code source est créé à ce moment-là.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
