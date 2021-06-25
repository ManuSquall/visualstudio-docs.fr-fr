---
title: Fonctions de l’API du plug-in de contrôle de code source | Microsoft Docs
description: En savoir plus sur les fonctions fournies par l’API de plug-in de contrôle de code source, qui doit être implémentée par le plug-in de contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f93ddff78aa151218d0b46d017e4631d9489e44
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899600"
---
# <a name="source-control-plug-in-api-functions"></a>Fonctions d’API du plug-in de contrôle de code source
L’API de plug-in de contrôle de code source fournit les fonctions suivantes, qui doivent être implémentées par le plug-in de contrôle de code source conformément à cette API. Les signatures de chaque fonction et la sémantique associée aux indicateurs binaires et à d’autres paramètres sont décrites en détail dans cette référence.

## <a name="initialization-and-housekeeping-functions"></a>Fonctions d’initialisation et de nettoyage

|Fonction|Description|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Ferme un projet.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Invite l’utilisateur à fournir des options avancées pour la commande donnée.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retourne la version du plug-in de contrôle de code source.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialise le plug-in de contrôle de code source. Elle est appelée une fois pour chaque instance du plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Ouvre un projet.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Fonction générique utilisée pour définir un large éventail d’options. Chaque option commence par `SCC_OPT_xxx` et possède son propre ensemble de valeurs défini.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Appelé une fois quand un plug-in de contrôle de code source doit être débranché.|

## <a name="core-source-control-functions"></a>Fonctions principales de contrôle de code source

|Fonction|Description|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Ajoute un tableau de fichiers spécifiés par des noms de chemins d’accès qualifiés complets au système de contrôle de code source.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permet à l’utilisateur de rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source, puis d’en faire partie du projet actif.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Archive un tableau de fichiers.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Extrait un tableau de fichiers.|
|[SccDiff](../extensibility/sccdiff-function.md)|Affiche les différences entre le fichier de l’utilisateur local spécifié par un nom de chemin d’accès qualifié complet et la version sous contrôle de code source.|
|[SccGet](../extensibility/sccget-function.md)|Récupère une copie en lecture seule d’un ensemble de fichiers.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Vérifie l’état des fichiers que l’appelant a demandés (via `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Fait en sorte que le plug-in de contrôle de code source invite l’utilisateur à indiquer un chemin d’accès au projet qui est significatif pour le plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Affiche l’historique d’un tableau de noms de fichiers locaux complets.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examine la liste des fichiers pour connaître leur état actuel. En outre, utilise la `pfnPopulate` fonction pour notifier l’appelant lorsqu’un fichier ne correspond pas aux critères de `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Affiche les propriétés d’un fichier complet.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examine une liste de fichiers complets pour leur état actuel.|
|[SccRemove](../extensibility/sccremove-function.md)|Supprime le tableau de fichiers qualifiés complets du système de contrôle de code source.|
|[SccRename](../extensibility/sccrename-function.md)|Renomme le fichier donné avec un nouveau nom dans le système de contrôle de code source.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accède à la gamme complète des fonctionnalités du système de contrôle de code source.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annule l’extraction d’un tableau de fichiers.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge des fonctionnalités supplémentaires (version 1,2 de l’API de plug-in de contrôle de code source)
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1,2 de l’API de plug-in de contrôle de code source. Ils fournissent un accès à des fonctionnalités et des fonctionnalités de contrôle de code source plus avancées.

|Fonction|Description|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Démarre une opération de traitement par lots.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crée un sous-projet portant le nom donné sous un projet parent existant.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Affiche les différences entre le répertoire de l’utilisateur local spécifié par un nom de chemin d’accès qualifié complet et l’emplacement de la base de données de contrôle de code source.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examine une liste de répertoires complets pour leur état actuel.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Met fin à une opération de traitement par lots.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retourne le chemin d’accès parent du projet donné (le projet doit exister).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Vérifie si plusieurs extractions sur un fichier sont autorisées.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Vérifie si le plug-in va créer MSSCCPRJ. Fichiers SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Fonctions qui prennent en charge la fonctionnalité avancée (version 1,3 de l’API de plug-in de contrôle de code source)
 Ce groupe de fonctions définit les fonctionnalités supplémentaires incluses dans la version 1,3 de l’API de plug-in de contrôle de code source. Ils fournissent un accès à des fonctionnalités et des fonctionnalités de contrôle de code source plus avancées.

|Fonction|Description|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Ajoute une liste de fichiers du contrôle de code source au projet en cours.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Récupère une liste de fichiers du contrôle de code source sans interface utilisateur.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Récupère une liste de fichiers dans le contrôle de code source qui sont différents des fichiers locaux.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Récupère les indicateurs qui spécifient les fonctionnalités étendues prises en charge par le plug-in de contrôle de code source.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Récupère les options spécifiques à l’utilisateur.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examine une liste de répertoires et de fichiers dans un projet ou des projets qui sont sous contrôle de code source. Chaque nom de répertoire et de fichier trouvé est passé à une fonction de rappel.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examine les modifications de nom apportées à une liste de fichiers. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.|

## <a name="requirements"></a>Spécifications
 En-tête : SCC. h

 (Fourni dans le dossier Common includes du kit de développement logiciel (SDK) Environment, par défaut *[lecteur]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc ; également fourni dans le dossier VSIP avec l’exemple MSSCCI, *[lecteur]* \Program Files\VSIP 8.0 \ MSSCCI).

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)
