---
title: Indicateurs de capacité | Microsoft Docs
description: En savoir plus sur les indicateurs de SCC_CAP_xxx qui indiquent les fonctionnalités d’un plug-in de contrôle de code source et les indicateurs SCC_EXCAP_xxx qui indiquent des fonctionnalités étendues.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdb660fd4e7c595f522686280f8bec6c0acae81
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905096"
---
# <a name="capability-flags"></a>Indicateurs de capacité
Les indicateurs SCC_CAP_ *xxx* sont des indicateurs de bits utilisés pour indiquer les fonctionnalités d’un plug-in de contrôle de code source. Les indicateurs SCC_EXCAP_ *xxx* sont des indicateurs incrémentiels qui indiquent des capacités étendues et sont résolus en valeurs entières.

|Code de capacité|Valeur|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Prend en charge [SccRemove](../extensibility/sccremove-function.md) et la commande.|
|`SCC_CAP_RENAME`|0x00000002L|Prend en charge [SccRename](../extensibility/sccrename-function.md) et la commande.|
|`SCC_CAP_DIFF`|0x00000004L|Prend en charge [SccDiff](../extensibility/sccdiff-function.md) et la commande.|
|`SCC_CAP_HISTORY`|0x00000008L|Prend en charge [SccHistory](../extensibility/scchistory-function.md) et la commande.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Prend en charge [SccProperties](../extensibility/sccproperties-function.md) et la commande.|
|`SCC_CAP_RUNSCC`|0x00000020L|Prend en charge [SccRunScc](../extensibility/sccrunscc-function.md) et la commande.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Prend en charge [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et la commande.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Prend en charge [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et la commande.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Prend en charge [SccGetEvents](../extensibility/sccgetevents-function.md) et la commande.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Prend en charge [SccGetProjPath](../extensibility/sccgetprojpath-function.md) et la commande.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Prend en charge [SccAddFromScc](../extensibility/sccaddfromscc-function.md) et la commande.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Prend en charge un commentaire sur l’extraction.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Prend en charge un commentaire sur l’archivage.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Prend en charge un commentaire sur Add.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Prend en charge un commentaire sur Remove.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Écrit du texte dans une fonction de sortie fournie par l’IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Prend en charge le stockage de fichiers sans Delta.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Prend en charge plusieurs historiques de fichiers.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Prend en charge la comparaison de fichiers ne respectant pas la casse.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Prend en charge la comparaison de fichiers qui ignore les espaces blancs.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Prend en charge la recherche de fichiers supplémentaires.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Prend en charge les commentaires sur la création de projet.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Prend en charge la comparaison dans tous les États s’il est sous contrôle.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Le plug-in ne prend pas en charge l’interface utilisateur pour obtenir, mais l’IDE peut toujours appeler [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Le plug-in est réentrant et thread-safe. Dans la version 1,0, aucun plug-in n’était supposé être réentrant et thread-safe. Si un plug-in 1,1 définit ce bit, l’hôte est autorisé à ouvrir plusieurs projets en parallèle.|

## <a name="capability-bits-added-in-version-12"></a>Fonctionnalités bits ajoutées dans la version 1,2

|Code de capacité|Valeur|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Prend en charge [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Prend en charge [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Prend en charge [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Prend en charge [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Prend en charge [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Prend en charge plusieurs extractions sur un fichier et le [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Prend en charge le fichier *Mssccprj. SCC* (soumis aux remplacements utilisateur/administrateur) et [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Fonctionnalités bits ajoutées dans la version 1,3
 Ces indicateurs sont passés un à la fois à la fonction [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) pour déterminer si la fonctionnalité est prise en charge.

|Code de capacité étendu|Valeur|Description|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Prend en charge l' `SCC_CHECKOUT_LOCALVER` option d’extraction.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Prend en charge [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Prend en charge [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Prend en charge la recherche de répertoires supplémentaires.|
|`SCC_EXCAP_QUERYCHANGES`|5|Prend en charge l’énumération des modifications de fichier.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Prend en charge [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Prend en charge [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Prend en charge l’appel de SccQueryInfo sur plusieurs threads.|
|`SCC_EXCAP_REMOVE_DIR`|9|Prend en charge la fonction SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Peut supprimer des fichiers extraits.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Peut renommer des fichiers extraits.|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
