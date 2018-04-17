---
title: Fonctions d’API de plug-in de contrôle de source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a834c4352ea2444c2669a57f760ed373999b07dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-plug-in-api-functions"></a>Fonctions d’API de plug-in de contrôle de source
L’API de plug-in de contrôle de Source fournit les fonctions suivantes, qui doivent être implémentées par le plug-in conformément à cette API de contrôle de code source. Les signatures de chaque fonction et la sémantique associées avec les indicateurs de bits et autres paramètres sont décrits en détail dans cette référence.  
  
## <a name="initialization-and-housekeeping-functions"></a>L’initialisation et les fonctions de maintenance  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Ferme un projet.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Invite l’utilisateur pour les options avancées pour la commande donnée.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retourne la version du contrôle de source de plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialise le plug-in de contrôle de code source. Elle est appelée une fois pour chaque instance du plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Ouvre un projet.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Une fonction générique utilisée pour définir un large éventail d’options. Chaque option commence par `SCC_OPT_xxx` et a son propre jeu défini de valeurs.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Appelée lorsqu’un plug-in de contrôle de code source doit être déconnecté.|  
  
## <a name="core-source-control-functions"></a>Fonctions de contrôle de Source de base  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Ajoute un tableau de fichiers spécifiés par les noms de chemin d’accès complet au système de contrôle de code source.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permet à l’utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis rendez ces dans les fichiers du projet actuel.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Recherche dans un tableau de fichiers.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Récupère un tableau de fichiers.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Indique les différences entre le fichier de l’utilisateur local spécifié par un nom de chemin d’accès complet et la version sous contrôle de code source.|  
|[SccGet](../extensibility/sccget-function.md)|Récupère une copie en lecture seule d’un ensemble de fichiers.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Vérifie l’état des fichiers qui a demandé à l’appelant sur (via `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Provoque le plug-in pour inviter l’utilisateur à un chemin d’accès de projet qui est significatif pour le plug-in de contrôle de code source.|  
|[SccHistory](../extensibility/scchistory-function.md)|Affiche l’historique pour un tableau de noms de fichiers local qualifié complet.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` fonction pour notifier l’appelant quand un fichier ne correspond pas les critères pour le `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Affiche les propriétés d’un fichier qualifié complet.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examine la liste des fichiers qualifiés complets pour leur état actuel.|  
|[SccRemove](../extensibility/sccremove-function.md)|Supprime le tableau de fichiers qualifiés complets à partir du système de contrôle de code source.|  
|[SccRename](../extensibility/sccrename-function.md)|Renomme le fichier donné à un nouveau nom dans le système de contrôle de code source.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accède à la gamme complète des fonctionnalités du système de contrôle de code source.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annule une extraction d’un tableau de fichiers.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge des fonctions supplémentaires (Version 1.2 de l’API de plug-in de contrôle de Source)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.2 de l’API de plug-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités et des fonctionnalités de contrôle de code source plus avancées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Démarre une opération de traitement par lots.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crée un sous-projet portant le nom indiqué sous un projet parent existant.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Indique les différences entre le répertoire de l’utilisateur local spécifié par un nom de chemin d’accès complet et l’emplacement de base de données de contrôle de code source.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examine une liste de répertoires complets pour leur état actuel.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termine une opération de traitement par lots.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retourne parente le chemin d’accès du projet donné (le projet doit exister).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Vérifie si les extractions multiples sur un fichier sont autorisées.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Vérifie si le plug-in crée MSSCCPRJ. Fichiers de contrôle de code source.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge des fonctionnalités avancées (Version 1.3 de l’API de plug-in de contrôle de Source)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.3 de l’API de plug-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités et des fonctionnalités de contrôle de code source plus avancées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers à partir du contrôle de code source pour le projet actuel.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Récupère une liste de fichiers à partir du contrôle de code source sans interface utilisateur.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Récupère une liste de fichiers dans le contrôle de code source qui sont différents des fichiers locaux.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Récupère les indicateurs qui spécifient les capacités étendues prises en charge par le plug-in de contrôle de code source.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Récupère les options spécifiques à l’utilisateur.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examine la liste des répertoires et des fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de répertoire et fichier trouvé est passé à une fonction de rappel.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examine les modifications apportées à une liste des fichiers aux noms. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : scc.h  
  
 (Fourni dans le SDK de l’environnement commun inclut le dossier, par défaut *[lecteur]*\Program Files\VSIP 8.0\EnvSDK\common\inc ; également fourni dans le dossier VSIP avec l’exemple MSSCCI, *[lecteur]*\Program 8.0\MSSCCI Files\VSIP).  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)