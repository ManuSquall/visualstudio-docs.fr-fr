---
title: Fonction de SccGetParentProjectPath | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea52e0d4c6242c57447cd47d41b716ba5e93a2f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142025"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath (fonction)
Cette fonction détermine le chemin d’accès du projet parent d’un projet spécifié. Cette fonction est appelée lorsque l’utilisateur ajoute un projet Visual Studio pour le contrôle de code source.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [dans, out] Le nom d’utilisateur (jusqu'à SCC_USER_SIZE, y compris la marque de fin NULL).  
  
 lpProjPath  
 [in] Chaîne qui identifie le chemin d’accès de projet (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
 lpAuxProjPath  
 [dans, out] Chaîne d’auxiliaire qui identifie le projet (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
 lpParentProjPath  
 [dans, out] Chaîne de sortie identifiant le chemin d’accès du projet parent (jusqu'à SCC_PRJPATH_SIZE, y compris la marque de fin NULL).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Chemin d’accès du projet parent a été obtenue avec succès.|  
|SCC_E_INITIALIZEFAILED|Projet n’a pas pu être initialisé.|  
|SCC_E_INVALIDUSER|L’utilisateur n’a pas pu se connecter le contrôle de code source du plug-in.|  
|SCC_E_UNKNOWNPROJECT|Projet est inconnu pour le plug-in de contrôle de code source.|  
|SCC_E_INVALIDFILEPATH|Chemin d’accès de fichier non valide ou inutilisable.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJSYNTAXERR|Syntaxe de projet non valide.|  
|SCC_E_CONNECTIONFAILURE|Problème de connexion de magasin.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction retourne un code de réussite ou l’échec et, en cas de réussite, remplit la variable `lpParentProjPath` avec le chemin d’accès de projet complet pour le projet spécifié.  
  
 Cette fonction retourne le parent de chemin d’accès de projet d’un projet existant. Pour le projet racine, la fonction retourne le chemin d’accès de projet qui a été passé (autrement dit, le même projet chemin racine). Notez qu’un chemin d’accès de projet est une chaîne qui est uniquement explicite pour le plug-in de contrôle de code source.  
  
 L’IDE est prête à accepter les modifications apportées à la `lpUser` et `lpAuxProjPath` également les paramètres. L’IDE est conservées de ces chaînes et les passer à la [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque l’utilisateur ouvre ce projet à l’avenir. Ces chaînes, par conséquent, permettent de pour le plug-in pour les informations de suivi nécessaires à associer à un projet de contrôle de code source.  
  
 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu’il n’affiche aucune invite l’utilisateur à sélectionner un projet. Il crée également jamais un projet mais fonctionne uniquement avec un projet existant.  
  
 Lorsque `SccGetParentProjectPath` est appelée, `lpProjPath` et `lpAuxProjPath` ne sera pas vide et correspond à un projet valide. Ces chaînes sont généralement reçus par l’IDE à partir d’un appel précédent à la `SccGetProjPath` (fonction).  
  
 Le `lpUser` argument est le nom d’utilisateur. L’IDE passe dans le même nom d’utilisateur qui il a précédemment reçu à partir de la `SccGetProjPath` (fonction) et le plug-in de contrôle de code source doivent utiliser le nom par défaut. Si l’utilisateur possède déjà une connexion ouverte avec le plug-in, le plug-in doit essayer d’éliminer les invites pour vous assurer que la fonction s’exécute en mode silencieux. Toutefois, si la connexion échoue, le plug-in doit inviter l’utilisateur pour un compte de connexion et, lorsqu’il reçoit une connexion valide, passez le nom du nouveau `lpUser`. Étant donné que le plug-in peut modifier cette chaîne, l’IDE toujours alloue une mémoire tampon de taille (`SCC_USER_LEN`+ 1). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide (au moins comme étant valide en tant que l’ancienne chaîne).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notes techniques pour SccCreateSubProject et SccGetParentProjectPath  
 Ajout de solutions et projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où qu'un utilisateur est invité à sélectionner les emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio, si un plug-in de contrôle de code source prend en charge des nouvelles fonctions, les [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) et `SccGetParentProjectPath` (fonction). Toutefois, l’entrée de Registre suivante peut être utilisée pour désactiver ces modifications et rétablir le comportement précédent de Visual Studio (Source de contrôle du plug-in API Version 1.1) :  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] « DoNotCreateSolutionRootFolderInSourceControl » = DWORD : 00000001  
  
 Si cette entrée de Registre n’existe pas ou a la valeur DWORD : 00000000, Visual Studio tente d’utiliser les nouvelles fonctions, `SccCreateSubProject`et`SccGetParentProjectPath`.  
  
 Si l’entrée de Registre a la valeur DWORD : 00000001, Visual Studio n’essaie pas d’utiliser ces nouvelles fonctions et les opérations d’ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)