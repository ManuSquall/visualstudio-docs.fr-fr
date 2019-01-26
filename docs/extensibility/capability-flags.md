---
title: Indicateurs de capacité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfbc456ea42342187b5d1d3039c10b3336714133
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934190"
---
# <a name="capability-flags"></a>Indicateurs de capacité
Le SCC_CAP_*xxx* indicateurs sont des indicateurs de bits utilisés pour indiquer les fonctionnalités d’un plug-in de contrôle de code source. Le SCC_EXCAP_*xxx* indicateurs sont incrémentielles indicateurs qui indiquent les capacités étendues et les résoudre en valeurs entières.  
  
|Code de fonctionnalité|Value|Description|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Prend en charge la [SccRemove](../extensibility/sccremove-function.md) et commande.|  
|`SCC_CAP_RENAME`|0x00000002L|Prend en charge la [SccRename](../extensibility/sccrename-function.md) et commande.|  
|`SCC_CAP_DIFF`|0x00000004L|Prend en charge la [SccDiff](../extensibility/sccdiff-function.md) et commande.|  
|`SCC_CAP_HISTORY`|0x00000008L|Prend en charge la [SccHistory](../extensibility/scchistory-function.md) et commande.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Prend en charge la [SccProperties](../extensibility/sccproperties-function.md) et commande.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Prend en charge la [SccRunScc](../extensibility/sccrunscc-function.md) et commande.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Prend en charge la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et commande.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Prend en charge la [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et commande.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Prend en charge la [SccGetEvents](../extensibility/sccgetevents-function.md) et commande.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Prend en charge la [SccGetProjPath](../extensibility/sccgetprojpath-function.md) et commande.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Prend en charge la [SccAddFromScc](../extensibility/sccaddfromscc-function.md) et commande.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Prend en charge un commentaire lors de l’extraction.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Prend en charge un commentaire sur l’archivage.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Prend en charge un commentaire sur Ajouter.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Prend en charge un commentaire sur Supprimer.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Écrit du texte dans une fonction de sortie fourni par l’IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Prend en charge le stockage des fichiers sans les deltas.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Prend en charge plusieurs l’historique des fichiers.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Prend en charge la comparaison de fichiers respectant la casse.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Prend en charge la comparaison qui ignore l’espace blanc de fichiers.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Prend en charge la recherche de fichiers supplémentaires.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Prend en charge les commentaires sur Créer un projet.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Prend en charge diff dans tous les États si sous contrôle.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Plug-in ne prend pas en charge une interface utilisateur pour Get, mais IDE peut toujours appeler [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Plug-in est réentrant et thread-safe. Dans la version 1.0, sans plug-ins sont considérés comme réentrant et thread-safe. Si un plug-in de 1.1 définit ce bit, l’hôte est autorisé à ouvrir plusieurs projets en parallèle.|  
  
## <a name="capability-bits-added-in-version-12"></a>Bits de fonctionnalité ajoutées dans la version 1.2  
  
|Code de fonctionnalité|Value|Description|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Prend en charge la [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Prend en charge la [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Prend en charge la [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Prend en charge la [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Prend en charge la [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Prend en charge les extractions multiples sur un fichier et le [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Prend en charge la *MSSCCPRJ.SCC* fichier (en fonction de substitution par l’utilisateur/administrateur) et le [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Bits de fonctionnalité ajoutées dans la version 1.3  
 Ces indicateurs sont passées à la fois pour le [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) fonction permettant de déterminer si la fonctionnalité est prise en charge.  
  
|Code de la capacité d’étendue|Value|Description|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Prend en charge la `SCC_CHECKOUT_LOCALVER` option des extractions.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Prend en charge la [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Prend en charge la [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Prend en charge la recherche de répertoires supplémentaires.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Prend en charge l’énumération des modifications de fichier.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Prend en charge la [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Prend en charge la [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Prend en charge l’appel de SccQueryInfo sur plusieurs threads.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Prend en charge la fonction SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Peut supprimer les fichiers extraits.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Pouvez renommer les fichiers extraits.|  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)