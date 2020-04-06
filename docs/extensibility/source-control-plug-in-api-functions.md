---
title: Fonctions d’API de contrôle des sources Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699919"
---
# <a name="source-control-plug-in-api-functions"></a>Fonctions d’API du plug-in de contrôle de code source
L’API de contrôle source fournit les fonctions suivantes, qui doivent être implémentées par le plug-in de contrôle source conformément à cette API. Les signatures de chaque fonction et de la sémantique associées aux drapeaux bits et à d’autres paramètres sont décrites en détail dans cette référence.

## <a name="initialization-and-housekeeping-functions"></a>Fonctions d’initialisation et d’entretien ménager

|Fonction|Description|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Ferme un projet.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Invite l’utilisateur à rechercher des options avancées pour la commande donnée.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retourne la version du plug-in de contrôle source.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialise le plug-in de contrôle source. Il est appelé une fois pour chaque cas du plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Ouvre un projet.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Une fonction générique utilisée pour définir une grande variété d’options. Chaque option `SCC_OPT_xxx` commence par et a son propre ensemble défini de valeurs.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Appelé une fois quand un plug-in de contrôle source doit être débranché.|

## <a name="core-source-control-functions"></a>Fonctions de contrôle des sources de base

|Fonction|Description|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Ajoute une gamme de fichiers spécifiés par des noms de chemin entièrement qualifiés au système de contrôle source.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permet à l’utilisateur de parcourir les fichiers qui sont déjà dans le système de contrôle source, puis de faire de ces fichiers une partie du projet en cours.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Vérifie dans une panoplie de fichiers.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Vérifie une gamme de fichiers.|
|[SccDiff](../extensibility/sccdiff-function.md)|Affiche les différences entre le fichier de l’utilisateur local spécifié par un nom de chemin entièrement qualifié et la version sous contrôle source.|
|[SccGet](../extensibility/sccget-function.md)|Récupère une copie de lecture seulement d’un ensemble de fichiers.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Vérifie l’état des fichiers que l’appelant a demandé (via `SccQueryInfo`).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Provoque le plug-in de contrôle source pour inciter l’utilisateur pour un chemin de projet qui est significatif pour le plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Montre l’histoire d’une gamme de noms de fichiers locaux entièrement qualifiés.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examine la liste des fichiers pour leur état actuel. En outre, `pfnPopulate` utilise la fonction pour informer l’appelant quand un `nCommand`fichier ne correspond pas aux critères pour le .|
|[SccProperties](../extensibility/sccproperties-function.md)|Affiche les propriétés d’un fichier entièrement qualifié.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examine une liste de fichiers entièrement qualifiés pour leur statut actuel.|
|[SccRemove](../extensibility/sccremove-function.md)|Supprime la gamme de fichiers entièrement qualifiés du système de contrôle source.|
|[SccRename](../extensibility/sccrename-function.md)|Renomme le fichier donné à un nouveau nom dans le système de contrôle source.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accéde à toute la gamme des fonctionnalités du système de contrôle source.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annule une caisse d’une série de fichiers.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge la capacité supplémentaire (Version 1.2 de l’API rechargeable de contrôle source)
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.2 de l’API de contrôle source plug-in. Ils donnent accès à des fonctionnalités et des capacités de contrôle source plus avancées.

|Fonction|Description|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Démarre une opération par lots.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crée un sous-projet avec le nom donné dans le cadre d’un projet parent existant.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Affiche les différences entre l’annuaire de l’utilisateur local spécifié par un nom de voie entièrement qualifié et l’emplacement de la base de données de contrôle source.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examine une liste d’annuaires entièrement qualifiés pour leur statut actuel.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termine une opération par lots.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retourne le parcours parent du projet donné (le projet doit exister).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Vérifie si plusieurs caisses sur un fichier sont autorisées.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Vérifie si le plug-in créera MSSCCPRJ. Fichiers CSC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge la capacité avancée (Version 1.3 de l’API rechargeable de contrôle source)
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1.3 de l’API de contrôle source plug-in. Ils donnent accès à des fonctionnalités et des capacités de contrôle source plus avancées.

|Fonction|Description|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers allant du contrôle source au projet en cours.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Récupère une liste de fichiers à partir du contrôle source sans interface utilisateur.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Récupère une liste de fichiers sous contrôle source qui sont différents des fichiers locaux.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Récupère les drapeaux qui spécifient les capacités étendues prises en charge par le plug-in de contrôle source.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Récupère les options spécifiques à l’utilisateur.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examine une liste d’annuaires et de fichiers dans un projet ou des projets qui sont sous contrôle source. Chaque répertoire et nom de fichier trouvé est transmis à une fonction de rappel.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examine les modifications de nom apportées à une liste de fichiers. Chaque nom de fichier est transmis à une fonction de rappel avec son statut de changement.|

## <a name="requirements"></a>Spécifications
 En-tête: scc.h

 (Fourni dans l’environnement SDK commun comprend dossier, par défaut *[lecteur]*'Fichiers de programme 'VSIP 8.0 'EnvSDK’commun’inc; également fourni dans le dossier VSIP avec l’échantillon MSSCCI, *[drive]*'Program Files’VSIP 8.0'MSSCCI).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)
