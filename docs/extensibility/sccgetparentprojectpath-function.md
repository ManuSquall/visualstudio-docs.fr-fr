---
title: "SccGetParentProjectPath (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath (fonction)"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccGetParentProjectPath (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction détermine le chemin d'accès du projet parent d'un projet spécifié. Cette fonction est appelée lorsque l'utilisateur ajoute un projet Visual Studio pour le contrôle de code source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpUser  
 \[dans, out\] Le nom d'utilisateur \(jusqu'à SCC\_USER\_SIZE, y compris le terminateur NULL\).  
  
 lpProjPath  
 \[in\] Chaîne qui identifie le chemin d'accès de projet \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpAuxProjPath  
 \[dans, out\] Chaîne auxiliaire qui identifie le projet \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
 lpParentProjPath  
 \[dans, out\] Chaîne de sortie qui identifie le chemin d'accès du projet parent \(jusqu'à SCC\_PRJPATH\_SIZE, y compris le terminateur NULL\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Chemin d'accès du projet parent a été obtenue avec succès.|  
|SCC\_E\_INITIALIZEFAILED|Projet n'a pas pu être initialisé.|  
|SCC\_E\_INVALIDUSER|L'utilisateur n'a pas pu se connecter le plug\-in de contrôle de code source.|  
|SCC\_E\_UNKNOWNPROJECT|Projet est inconnu pour le plug\-in de contrôle de code source.|  
|SCC\_E\_INVALIDFILEPATH|Chemin d'accès de fichier non valide ou inutilisable.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC\_E\_PROJSYNTAXERR|Syntaxe de projet non valide.|  
|SCC\_E\_CONNECTIONFAILURE|Problème de connexion du magasin.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Erreur non spécifique.|  
  
## Notes  
 Cette fonction retourne un code de réussite ou l'échec et, en cas de réussite, remplit la variable `lpParentProjPath` avec le chemin d'accès complet de projet au projet spécifié.  
  
 Cette fonction retourne le parent de chemin d'accès de projet d'un projet existant. Pour le projet racine, la fonction retourne le chemin d'accès de projet qui a été passé \(autrement dit, le même projet chemin racine\). Notez qu'un chemin d'accès de projet est une chaîne qui est uniquement explicite pour le plug\-in de contrôle de code source.  
  
 L'IDE est prête à accepter les modifications apportées à la `lpUser` et `lpAuxProjPath` ainsi les paramètres. L'IDE est conserver ces chaînes et les passer à la [SccOpenProject](../extensibility/sccopenproject-function.md) lorsque l'utilisateur ouvre ce projet à l'avenir. Ces chaînes permettent par conséquent, pour le plug\-in pour les informations de suivi nécessaires à associer à un projet de contrôle de code source.  
  
 Cette fonction est similaire à la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), sauf qu'il ne demande pas l'utilisateur de sélectionner un projet. Il crée également jamais un projet mais fonctionne uniquement avec un projet existant.  
  
 Lorsque `SccGetParentProjectPath` est appelée, `lpProjPath` et `lpAuxProjPath` ne sera pas vide et correspond à un projet valide. Ces chaînes sont généralement reçus par l'IDE à partir d'un appel précédent à la `SccGetProjPath` \(fonction\).  
  
 Le `lpUser` argument est le nom d'utilisateur. L'IDE passe dans le même nom d'utilisateur qui il a précédemment reçu à partir de la `SccGetProjPath` \(fonction\) et le plug\-in de contrôle de code source doivent utiliser le nom par défaut. Si l'utilisateur dispose déjà d'une connexion ouverte avec le plug\-in, le plug\-in doit essayer d'éliminer les invites pour vous assurer que la fonction s'exécute en mode silencieux. Toutefois, si la connexion échoue, le plug\-in doit inviter l'utilisateur pour un compte de connexion et, lorsqu'il reçoit une connexion valide, passez le nom du nouveau `lpUser`. Étant donné que le plug\-in peut modifier cette chaîne, l'IDE sera toujours allouer un tampon de taille \(`SCC_USER_LEN`\+ 1\). Si la chaîne est modifiée, la nouvelle chaîne doit être un nom de connexion valide \(au moins aussi valide en tant que l'ancienne chaîne\).  
  
## Notes techniques de SccCreateSubProject et SccGetParentProjectPath  
 Ajout de solutions et projets au contrôle de code source a été simplifié dans Visual Studio afin de réduire le nombre de fois où qu'un utilisateur est invité à sélectionner les emplacements dans le système de contrôle de code source. Ces modifications sont activées par Visual Studio si un plug\-in de contrôle de code source prend en charge deux nouvelles fonctions, le [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) et le `SccGetParentProjectPath` \(fonction\). Toutefois, l'entrée de Registre suivante peut servir à désactiver ces modifications et rétablir le comportement précédent de Visual Studio \(Source contrôle plug\-in API Version 1.1\) :  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] « DoNotCreateSolutionRootFolderInSourceControl » \= DWORD: 00000001  
  
 Si cette entrée de Registre n'existe pas ou a la valeur DWORD: 00000000, Visual Studio tente d'utiliser les nouvelles fonctions, `SccCreateSubProject`et`SccGetParentProjectPath`.  
  
 Si l'entrée de Registre est définie à DWORD: 00000001, Visual Studio n'essaie pas d'utiliser ces nouvelles fonctions et les opérations d'ajout au contrôle de code source fonctionnent comme dans les versions antérieures de Visual Studio.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)