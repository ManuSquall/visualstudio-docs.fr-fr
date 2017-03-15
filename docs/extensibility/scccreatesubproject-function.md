---
title: "SccCreateSubProject (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject (fonction)"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# SccCreateSubProject (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction crée un sous\-projet portant le nom spécifié dans un projet parent existant spécifié par le `lpParentProjPath` argument.  
  
## Syntaxe  
  
```cpp#  
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
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpUser  
 \[dans, out\] Le nom d'utilisateur \(jusqu'à SCC\_USER\_SIZE, y compris le terminateur NULL\).  
  
 lpParentProjPath  
 \[in\] Une chaîne qui identifie le chemin d'accès du projet parent \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpSubProjName  
 \[in\] Le nom suggéré sous\-projet \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpAuxProjPath  
 \[dans, out\] Chaîne auxiliaire qui identifie le projet \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpSubProjPath  
 \[dans, out\] Chaîne de sortie qui identifie le chemin d'accès pour le sous\-projet \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Sous\-projet a été créé avec succès.|  
|SCC\_E\_INITIALIZEFAILED|Projet parent n'a pas pu être initialisé.|  
|SCC\_E\_INVALIDUSER|L'utilisateur n'a pas pu se connecter le système de contrôle source.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Impossible de créer un sous\-projet.|  
|SCC\_E\_PROJSYNTAXERR|Syntaxe de projet non valide.|  
|SCC\_E\_UNKNOWNPROJECT|Le projet parent est inconnu pour le plug\-in de contrôle de code source.|  
|SCC\_E\_INVALIDFILEPATH|Chemin d'accès de fichier non valide ou inutilisable.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_CONNECTIONFAILURE|Il y a un problème de connexion plug\-in de contrôle de code source.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
  
## Notes  
 Si un sous\-projet portant le nom existe déjà, la fonction peut modifier le nom par défaut pour créer un unique, par exemple en ajoutant « \_ \< numéro \> » pour elle. L'appelant doit être préparé à accepter les modifications de `lpUser`, `lpSubProjPath`, et `lpAuxProjPath`. Le `lpSubProjPath` et`lpAuxProjPath` arguments sont ensuite utilisées dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). Ils ne doivent pas être modifiés par l'appelant lors du retour. Ces chaînes constituent un moyen pour le plug\-in pour le suivi des informations dont il a besoin à associer à un projet de contrôle de code source. L'appelant IDE n'affiche pas ces deux paramètres au moment du retour, car le plug\-in peut utiliser une chaîne de mise en forme qui peut ne pas convenir pour l'affichage. La fonction retourne un code de réussite ou l'échec et, en cas de réussite, remplit la variable `lpSubProjPath` avec le chemin d'accès de projet complet pour le nouveau projet.  
  
 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu'il crée en mode silencieux d'un projet plutôt que d'inviter l'utilisateur à sélectionner un. Lorsque le `SccCreateSubProject` fonction est appelée, `lpParentProjName` et `lpAuxProjPath` ne sera pas vide et correspond à un projet valide. Ces chaînes sont généralement reçus par l'IDE à partir d'un appel précédent à la `SccGetProjPath` fonction ou [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Le `lpUser` argument est le nom d'utilisateur. L'IDE passe dans le même nom d'utilisateur a précédemment reçu de `SccGetProjPath`, et le plug\-in de contrôle de code source doit utiliser le nom par défaut. Si l'utilisateur dispose déjà d'une connexion ouverte avec le plug\-in, le plug\-in doit essayer d'éliminer les invites pour vous assurer que la fonction s'exécute en mode silencieux. Toutefois, si la connexion échoue, le plug\-in doit inviter l'utilisateur pour un compte de connexion et, lorsqu'il reçoit une connexion valide, passez le nom du nouveau `lpUser`. Étant donné que le plug\-in peut modifier cette chaîne, l'IDE sera toujours allouer une mémoire tampon de taille \(SCC\_USER\_LEN \+ 1 ou SCC\_USER\_SIZE, qui inclut l'espace pour le terminateur null\). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide \(au moins aussi valide en tant que l'ancienne chaîne\).  
  
## Notes techniques de SccCreateSubProject et SccGetParentProjectPath  
 Ajout de solutions et projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où qu'un utilisateur est invité à sélectionner les emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio si un plug\-in de contrôle de code source prend en charge deux nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`. Toutefois, l'entrée de Registre suivante peut être utilisée pour désactiver ces modifications et revenir au comportement précédent de Visual Studio \(Source contrôle plug\-in API Version 1.1\) :  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] « DoNotCreateSolutionRootFolderInSourceControl » \= DWORD: 00000001  
  
 Si cette entrée de Registre n'existe pas ou a la valeur DWORD: 00000000, Visual Studio tente d'utiliser les nouvelles fonctions, `SccCreateSubProject` et `SccGetParentProjectPath`.  
  
 Si l'entrée de Registre est définie à DWORD: 00000001, Visual Studio n'essaie pas d'utiliser ces nouvelles fonctions et les opérations d'ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)