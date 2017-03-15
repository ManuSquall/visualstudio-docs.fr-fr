---
title: "Fonctions d&#39;API de plug-in de contr&#244;le de source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, fonctions"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Fonctions d&#39;API de plug-in de contr&#244;le de source
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'API de plug\-in de contrôle de Source fournit les fonctions suivantes, qui doivent être implémentées par le contrôle de code source du plug\-in conformément à cette API. Les signatures de chaque fonction et la sémantique associés avec les indicateurs de bits et les autres paramètres sont décrits en détail dans cette référence.  
  
## L'initialisation et les opérations de maintenance  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Ferme un projet.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Invite l'utilisateur pour les options avancées pour la commande donnée.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retourne la version du contrôle de source de plug\-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialise le plug\-in de contrôle de code source. Elle est appelée une fois pour chaque instance du plug\-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Ouvre un projet.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Une fonction générique utilisée pour définir un large éventail d'options. Chaque option commence par `SCC_OPT_xxx` et possède son propre jeu de valeurs défini.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Appelée lorsqu'un plug\-in de contrôle de code source a besoin d'être déconnecté.|  
  
## Fonctions de contrôle de Source de base  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Ajoute un tableau de fichiers spécifiés par les noms de chemin d'accès complet au système de contrôle source.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permet à l'utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis rendez partie de ces fichiers du projet actuel.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Recherche dans un tableau de fichiers.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Récupère un tableau de fichiers.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Indique les différences entre les fichiers de l'utilisateur local spécifié par un nom de chemin d'accès complet et la version sous contrôle de code source.|  
|[SccGet](../extensibility/sccget-function.md)|Récupère une copie en lecture seule d'un ensemble de fichiers.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Vérifie l'état des fichiers qui a demandé l'appelant sur \(via `SccQueryInfo`\).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Provoque le plug\-in pour inviter l'utilisateur à un chemin d'accès de projet qui est significatif pour le plug\-in de contrôle de code source.|  
|[SccHistory](../extensibility/scchistory-function.md)|Affiche l'historique pour un tableau de noms de fichier local complet.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` \(fonction\) pour notifier l'appelant quand un fichier ne respectent pas les critères pour le `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Affiche les propriétés d'un fichier complet.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examine une liste de fichiers complets pour leur état actuel.|  
|[SccRemove](../extensibility/sccremove-function.md)|Supprime le tableau de fichiers complètes du système de contrôle source.|  
|[SccRename](../extensibility/sccrename-function.md)|Renomme le fichier donné par un nouveau nom dans le système de contrôle de code source.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accède à la gamme complète des fonctionnalités du système de contrôle source.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annule une extraction d'un tableau de fichiers.|  
  
## Fonctions qui prennent en charge des fonctions supplémentaires \(Version 1.2 de l'API de plug\-in de contrôle de Source\)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.2 de l'API de plug\-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités de contrôle de code source et aux fonctionnalités plus avancées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Démarre une opération par lot.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crée un sous\-projet portant le nom spécifié dans un projet parent existant.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Affiche les différences entre le répertoire de l'utilisateur local spécifié par un nom de chemin d'accès complet et l'emplacement de base de données de contrôle de source.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examine une liste de répertoires complets pour leur état actuel.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termine une opération de traitement par lots.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retourne parente du projet donné \(le projet doit exister\).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Vérifie si les extractions multiples sur un fichier sont autorisées.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Vérifie si le plug\-in crée MSSCCPRJ. Fichiers de contrôle de code source.|  
  
## Fonctions qui prennent en charge les fonctionnalités avancées \(Version 1.3 de l'API de plug\-in de contrôle de Source\)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.3 de l'API de plug\-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités de contrôle de code source et aux fonctionnalités plus avancées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers à partir du contrôle de code source pour le projet actuel.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Récupère une liste de fichiers à partir du contrôle de code source sans interface utilisateur.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Récupère une liste de fichiers dans le contrôle de code source qui sont différents des fichiers locaux.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Récupère des indicateurs qui spécifient les fonctionnalités prises en charge par le plug\-in de contrôle de code source.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Récupère les options spécifiques à l'utilisateur.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examine une liste des répertoires et fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de fichier et de répertoire trouvé est passé à une fonction de rappel.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examine les modifications apportées à une liste de fichiers aux noms. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.|  
  
## Spécifications  
 En\-tête : scc.h  
  
 \(Fourni dans le Kit de développement environnement commun inclut le dossier, par défaut *\[lecteur\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc ; également fourni dans le dossier VSIP avec l'exemple MSSCCI, *\[lecteur\]*\\Program Files\\VSIP 8.0\\MSSCCI\).  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d'un contrôle de Source de plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)