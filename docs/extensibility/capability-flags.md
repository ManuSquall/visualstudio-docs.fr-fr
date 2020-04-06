---
title: Drapeaux de capacité Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739868"
---
# <a name="capability-flags"></a>Drapeaux de capacité
Les SCC_CAP_ des drapeaux*xxx* sont des drapeaux bit utilisés pour indiquer les capacités d’un plug-in de contrôle source. Les SCC_EXCAP_ des drapeaux*xxx* sont des drapeaux incrémentaux qui indiquent des capacités étendues et la résolution des valeurs d’intégrage.

|Code de capacité|Valeur|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Soutient le [SccRemove](../extensibility/sccremove-function.md) et le commandement.|
|`SCC_CAP_RENAME`|0x00000002L|Soutient le [SccRename](../extensibility/sccrename-function.md) et le commandement.|
|`SCC_CAP_DIFF`|0x00000004L|Soutient le [SccDiff](../extensibility/sccdiff-function.md) et le commandement.|
|`SCC_CAP_HISTORY`|0x00000008L|Soutient l’histoire et le commandement de [la Scc.](../extensibility/scchistory-function.md)|
|`SCC_CAP_PROPERTIES`|0x00000010L|Soutient les [SccProperties](../extensibility/sccproperties-function.md) et la commande.|
|`SCC_CAP_RUNSCC`|0x00000020L|Soutient le [SccRunScc](../extensibility/sccrunscc-function.md) et commande.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Soutient les [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et commande.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Prend en charge le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et la commande.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Soutient les [SccGetEvents](../extensibility/sccgetevents-function.md) et la commande.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Soutient le [SccGetProjPath](../extensibility/sccgetprojpath-function.md) et la commande.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Soutient le [SccAddDeScc](../extensibility/sccaddfromscc-function.md) et commande.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Prend en charge un commentaire à la caisse.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Prend en charge un commentaire sur checkin.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Soutient un commentaire sur Add.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Prend en charge un commentaire sur Supprimer.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Écrit du texte à une fonction de sortie fournie par l’IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Prend en charge le stockage des fichiers sans deltas.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Prend en charge l’historique de fichiers multiples.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Prend en charge la comparaison des dossiers insensibles aux cas.|
|`SCC_CAP_IGNORESPACE`|0x0100000L|Soutient la comparaison des fichiers qui ignore l’espace blanc.|
|`SCC_CAP_POPULATELIST`|0x0200000L|Prend en charge la recherche de fichiers supplémentaires.|
|`SCC_CAP_COMMENTPROJECT`|0x0400000L|Soutient les commentaires sur la création de projets.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Soutient le diff dans tous les États s’il est sous contrôle.|
|`SCC_CAP_GET_NOUI`|0x2000000L|Plug-in ne prend pas en charge une interface utilisateur pour Get, mais IDE peut encore appeler [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Le plug-in est réentrant et sans fil. Dans la version 1.0, aucun plug-ins n’a été supposé être réentrant et sans fil. Si un plug-in 1.1 définit ce bit, l’hôte est autorisé à ouvrir plusieurs projets en parallèle.|

## <a name="capability-bits-added-in-version-12"></a>Bits de capacité ajoutés dans la version 1.2

|Code de capacité|Valeur|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Soutient le [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Soutient le [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Soutient le [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et [le SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Prend en charge le [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Soutient le [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Prend en charge plusieurs caisses sur un fichier et le [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Prend en charge le fichier *MSSCCPRJ.SCC* (sous réserve de la dérogation utilisateur/administrateur) et le [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bits de capacité ajoutés dans la version 1.3
 Ces drapeaux sont transmis un à la fois à la fonction [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) pour déterminer si la capacité est prise en charge.

|Code de capacité étendu|Valeur|Description|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Prend `SCC_CHECKOUT_LOCALVER` en charge l’option pour les caisses.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Soutient le [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Prend en charge les [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Soutient la recherche d’annuaires supplémentaires.|
|`SCC_EXCAP_QUERYCHANGES`|5|Prend en charge l’énumération des modifications de fichiers.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Soutient le [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Soutient le [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Prend en charge l’appel de SccQueryInfo sur plusieurs threads.|
|`SCC_EXCAP_REMOVE_DIR`|9|Soutient la fonction SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Peut supprimer les fichiers vérifiés.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Peut renommer les fichiers vérifiés.|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
