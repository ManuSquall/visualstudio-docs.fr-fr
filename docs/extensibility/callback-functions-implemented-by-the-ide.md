---
title: "Fonctions de rappel impl&#233;ment&#233;es par l&#39;IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, les fonctions de rappel"
  - "fonctions de rappel, les plug-ins de contrôle de code source"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Fonctions de rappel impl&#233;ment&#233;es par l&#39;IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour faciliter l'intégration avec l'environnement de développement intégré \(IDE\) comme transparente que possible et pour fournir une expérience unifiée de l'utilisateur final, le plug\-in de contrôle de code source peut utiliser les fonctions de rappel sont implémentées par l'IDE. Le plug\-in peut appeler ces fonctions à des moments appropriés pendant une opération de contrôle de code source pour passer des informations à l'IDE ; l'IDE peut ensuite afficher ces informations comme éléments incorporés dans son interface utilisateur native. L'utilisateur profite d'une expérience moins fragmentée dans ce scénario que si le plug\-in employé sa propre interface utilisateur.  
  
 Le fichier d'en\-tête requis est scc.h. L'emplacement par défaut est \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\. Il est également dans le dossier VSIP doté de l'exemple de plug\-in de contrôle de code source à \\Program Files\\VSIP 8.0\\MSSCCI\\.  
  
## Dans cette section  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug\-in via l'IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccPopulateList](../extensibility/sccpopulatelist-function.md) lorsque l'environnement IDE n'a pas un accès complet aux informations qui sont uniquement disponibles pour le contrôle de code source du plug\-in, telles qu'une liste complète des fichiers sous contrôle de version.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Décrit la fonction de rappel qui est utilisée par le [SccQueryChanges](../extensibility/sccquerychanges-function.md) opération.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Décrit la fonction de rappel qui est utilisée par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) opération.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Décrit la fonction de rappel définie par un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) qui permet le contrôle de code source du plug\-in pour communiquer les modifications de nom dans l'IDE.  
  
## Rubriques connexes  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Ouvre un projet.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` \(fonction\) pour notifier l'appelant quand un fichier ne respectent pas les critères pour le `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examine une liste des répertoires et fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de fichier et de répertoire trouvé est passé à une fonction de rappel.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examine les modifications de nom qui ont été apportées à une liste de fichiers. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Définit un large éventail d'options. Chaque option commence par `SCC_OPT_xxx` et possède son propre jeu de valeurs défini.  
  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Décrit le contenu de la section de référence du Kit de développement du plug\-in de contrôle Source.