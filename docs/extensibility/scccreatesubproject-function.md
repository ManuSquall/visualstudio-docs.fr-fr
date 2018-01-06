---
title: Fonction de SccCreateSubProject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97993833d08479fbf518fb5b4852f46cc34f9bc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject (fonction)
Cette fonction crée un sous-projet portant le nom indiqué sous un projet parent existant spécifié par le `lpParentProjPath` argument.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [dans, out] Le nom d’utilisateur (jusqu'à SCC_USER_SIZE, y compris la marque de fin NULL).  
  
 lpParentProjPath  
 [in] Chaîne identifiant le chemin d’accès du projet parent (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
 lpSubProjName  
 [in] Le nom suggéré sous-projet (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
 lpAuxProjPath  
 [dans, out] Chaîne d’auxiliaire qui identifie le projet (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
 lpSubProjPath  
 [dans, out] Chaîne de sortie identifiant le chemin d’accès pour le sous-projet (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Sous-projet a été créé avec succès.|  
|SCC_E_INITIALIZEFAILED|Projet parent n’a pas pu être initialisé.|  
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter le système de contrôle source.|  
|SCC_E_COULDNOTCREATEPROJECT|Impossible de créer un sous-projet.|  
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|  
|SCC_E_UNKNOWNPROJECT|Le projet parent est inconnu pour le plug-in de contrôle de code source.|  
|SCC_E_INVALIDFILEPATH|Chemin d’accès de fichier non valide ou inutilisable.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_CONNECTIONFAILURE|Il y a un problème de connexion du plug-in de contrôle de code source.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Si un sous-projet portant le nom existe déjà, la fonction peut modifier le nom par défaut pour créer un unique, par exemple en ajoutant « _\<numéro > » à ce dernier. L’appelant doit être prêt à accepter les modifications de `lpUser`, `lpSubProjPath`, et `lpAuxProjPath`. Le `lpSubProjPath` et`lpAuxProjPath` arguments sont ensuite utilisées dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). Ils ne doivent pas être modifiés par l’appelant lors du retour. Ces chaînes constituent un moyen pour le plug-in pour le suivi des informations dont il a besoin à associer à un projet de contrôle de code source. L’appelant IDE n’affiche pas ces deux paramètres au moment du retour, car le plug-in peut utiliser une chaîne de mise en forme qui peut ne pas convenir pour l’affichage. La fonction retourne un code de réussite ou l’échec et, en cas de réussite, remplit la variable `lpSubProjPath` avec le chemin d’accès de projet complet pour le nouveau projet.  
  
 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu’il crée en mode silencieux un projet au lieu d’inviter l’utilisateur à sélectionner un. Lorsque le `SccCreateSubProject` fonction est appelée, `lpParentProjName` et `lpAuxProjPath` ne sera pas vide et correspond à un projet valide. Ces chaînes sont généralement reçus par l’IDE à partir d’un appel précédent à la `SccGetProjPath` fonction ou le [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Le `lpUser` argument est le nom d’utilisateur. Dans le même nom d’utilisateur qui il a précédemment reçu à partir de l’IDE passe `SccGetProjPath`, et le plug-in de contrôle de code source doit utiliser le nom par défaut. Si l’utilisateur possède déjà une connexion ouverte avec le plug-in, le plug-in doit essayer d’éliminer les invites pour vous assurer que la fonction s’exécute en mode silencieux. Toutefois, si la connexion échoue, le plug-in doit inviter l’utilisateur pour un compte de connexion et, lorsqu’il reçoit une connexion valide, passez le nom du nouveau `lpUser`. Étant donné que le plug-in peut modifier cette chaîne, l’IDE toujours alloue une mémoire tampon de taille (SCC_USER_LEN + 1 ou SCC_USER_SIZE, qui inclut un espace pour le terminateur null). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins comme étant valide en tant que l’ancienne chaîne).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath  
 Ajout de solutions et projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où qu'un utilisateur est invité à sélectionner les emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio, si un plug-in de contrôle de code source prend en charge des nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`. Toutefois, l’entrée de Registre suivante peut être utilisée pour désactiver ces modifications et de rétablir le comportement précédent de Visual Studio (Source de contrôle du plug-in API Version 1.1) :  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] « DoNotCreateSolutionRootFolderInSourceControl » = DWORD : 00000001  
  
 Si cette entrée de Registre n’existe pas ou a la valeur DWORD : 00000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`.  
  
 Si l’entrée de Registre a la valeur DWORD : 00000001, Visual Studio n’essaie pas d’utiliser ces nouvelles fonctions et les opérations d’ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)