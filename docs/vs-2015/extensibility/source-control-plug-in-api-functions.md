---
title: Fonctions d’API de plug-in de contrôle de source | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eadf9c76fcebe79eb8e8f599aecdf934485a34ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502359"
---
# <a name="source-control-plug-in-api-functions"></a>Fonctions d’API du plug-in de contrôle de code source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonctions de API de plug-in de contrôle Source](https://docs.microsoft.com/visualstudio/extensibility/source-control-plug-in-api-functions).  
  
L’API de plug-in de contrôle de Source fournit les fonctions suivantes, qui doivent être implémentées par le plug-in conformément à cette API de contrôle de code source. Les signatures de chaque fonction et la sémantique associées avec les indicateurs de bits et autres paramètres sont décrits en détail dans cette référence.  
  
## <a name="initialization-and-housekeeping-functions"></a>L’initialisation et fonctions de gestion interne  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Ferme un projet.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Invite l’utilisateur pour les options avancées pour la commande donnée.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retourne la version du contrôle de source de plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialise le plug-in de contrôle de code source. Elle est appelée une fois pour chaque instance du plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Ouvre un projet.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Une fonction générique utilisée pour définir un large éventail d’options. Chaque option commence par `SCC_OPT_xxx` et possède son propre ensemble défini de valeurs.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Appelée une fois lorsqu’un plug-in de contrôle de code source a besoin d’être déconnecté.|  
  
## <a name="core-source-control-functions"></a>Fonctions de contrôle de Source de base  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Ajoute un tableau de fichiers spécifiés par les noms de chemin d’accès complet au système de contrôle source.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permet à l’utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis rendez ces fichiers faisant partie du projet actuel.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Vérifie dans un tableau de fichiers.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Extrait un tableau de fichiers.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Montre les différences entre le fichier de l’utilisateur local spécifié par un nom de chemin d’accès complet et la version sous contrôle de code source.|  
|[SccGet](../extensibility/sccget-function.md)|Récupère une copie en lecture seule d’un ensemble de fichiers.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Vérifie l’état des fichiers qui a demandé l’appelant sur (via `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Provoque le plug-in pour inviter l’utilisateur pour un chemin d’accès de projet qui est significatif pour le plug-in de contrôle de code source.|  
|[SccHistory](../extensibility/scchistory-function.md)|Affiche l’historique pour un tableau de noms de fichier local complet.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examine la liste des fichiers pour leur état actuel. En outre, utilise le `pfnPopulate` fonction permettant de notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Présente les propriétés d’un fichier qualifié complet.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examine une liste de fichiers qualifiés complets pour leur état actuel.|  
|[SccRemove](../extensibility/sccremove-function.md)|Supprime le tableau de fichiers complets à partir du système de contrôle source.|  
|[SccRename](../extensibility/sccrename-function.md)|Renomme le fichier donné vers un nouveau nom dans le système de contrôle source.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accède à la gamme complète des fonctionnalités du système de contrôle source.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annule une extraction d’un tableau de fichiers.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge des fonctions supplémentaires (Version 1.2 de l’API de plug-in de contrôle de Source)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.2 de l’API de plug-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités de contrôle de code source et des fonctionnalités plus avancés.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Démarre une opération par lot.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crée un sous-projet portant le nom spécifié sous un projet parent existant.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Montre les différences entre le répertoire de l’utilisateur local spécifié par un nom de chemin d’accès complet et l’emplacement de base de données de contrôle de source.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examine une liste de répertoires complets pour leur état actuel.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termine une opération par lot.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retourne parents de chemin d’accès du projet donné (le projet doit exister).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Vérifie si les extractions multiples sur un fichier sont autorisées.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Vérifie si le plug-in crée MSSCCPRJ. Fichiers SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge la fonctionnalité avancée (Version 1.3 de l’API de plug-in de contrôle de Source)  
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.3 de l’API de plug-in de contrôle de Source. Ils fournissent un accès à des fonctionnalités de contrôle de code source et des fonctionnalités plus avancés.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers à partir du contrôle de code source au projet actuel.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Récupère une liste de fichiers à partir du contrôle de code source sans interface utilisateur.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Récupère une liste de fichiers dans le contrôle de code source qui sont différents des fichiers locaux.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Récupère les indicateurs qui spécifient les capacités étendues prises en charge par le plug-in de contrôle de code source.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Récupère les options spécifiques à l’utilisateur.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examine une liste de répertoires et fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de répertoire et fichier trouvé est passé à une fonction de rappel.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examine les modifications apportées à une liste des fichiers aux noms. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : scc.h  
  
 (Fourni dans le SDK de l’environnement commun inclut le dossier, par défaut *[lecteur]* \Program Files\VSIP 8.0\EnvSDK\common\inc ; également fourni dans le dossier VSIP avec l’exemple MSSCCI, *[lecteur]* \Program 8.0\MSSCCI Files\VSIP).  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)

