---
title: "Indicateurs de capacité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a438320fbfefac1e0104cd13012ace9573aa3742
ms.lasthandoff: 02/22/2017

---
# <a name="capability-flags"></a>Indicateurs de capacité
Le SCC_CAP_*xxx* indicateurs sont des bits indicateurs utilisés pour indiquer les fonctionnalités d’un plug-in de contrôle de code source. Le SCC_EXCAP_*xxx* indicateurs sont incrémentielles indicateurs qui indiquent les fonctions étendues et de résoudre en valeurs entières.  
  
|Code de fonction|Valeur|Description|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Prend en charge les [SccRemove](../extensibility/sccremove-function.md) et commande.|  
|`SCC_CAP_RENAME`|0x00000002L|Prend en charge les [SccRename](../extensibility/sccrename-function.md) et commande.|  
|`SCC_CAP_DIFF`|0x00000004L|Prend en charge les [SccDiff](../extensibility/sccdiff-function.md) et commande.|  
|`SCC_CAP_HISTORY`|0x00000008L|Prend en charge les [SccHistory](../extensibility/scchistory-function.md) et commande.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Prend en charge les [SccProperties](../extensibility/sccproperties-function.md) et commande.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Prend en charge les [SccRunScc](../extensibility/sccrunscc-function.md) et commande.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Prend en charge les [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et commande.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Prend en charge les [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et commande.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Prend en charge le [SccGetEvents](../extensibility/sccgetevents-function.md) et commande.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Prend en charge le [SccGetProjPath](../extensibility/sccgetprojpath-function.md) et commande.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Prend en charge les [SccAddFromScc](../extensibility/sccaddfromscc-function.md) et commande.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Prend en charge un commentaire sur l’extraction.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Prend en charge un commentaire sur l’archivage.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Prend en charge un commentaire sur Ajouter.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Prend en charge un commentaire sur Supprimer.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Écrit du texte dans une fonction de sortie fourni par l’IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Prend en charge le stockage des fichiers sans les deltas.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Prend en charge de l’historique des fichiers multiples.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Prend en charge la comparaison de fichiers de la casse.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Prend en charge de fichiers comparaison qui ignore l’espace blanc.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Prend en charge la recherche de fichiers supplémentaires.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Prend en charge les commentaires de créer le projet.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Prend en charge diff dans tous les États sous contrôle.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Plug-in ne prend pas en charge une interface utilisateur Get, mais IDE peut toujours appeler [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Plug-in est réentrant et thread-safe. Dans la version 1.0, aucun plug-in a été considéré comme réentrant et thread-safe. Si un plug-in de 1.1 définit ce bit, l’hôte est autorisé à ouvrir plusieurs projets en parallèle.|  
  
## <a name="capability-bits-added-in-version-12"></a>Bits de fonctionnalité ajoutées à la Version 1.2  
  
|Code de fonction|Valeur|Description|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Prend en charge les [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Prend en charge les [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Prend en charge les [SccBeginBatch](../extensibility/sccbeginbatch-function.md) et [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Prend en charge les [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Prend en charge les [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Prend en charge les extractions multiples sur un fichier et le [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Prend en charge la MSSCCPRJ. Fichier de contrôle de code source (soumis au remplacement de l’administrateur/utilisateur) et le [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Bits de fonctionnalité ajoutées dans la Version 1.3  
 Ces indicateurs sont passés à la fois pour le [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) fonction pour déterminer si la fonctionnalité est prise en charge.  
  
|Code de la capacité étendue|Valeur|Description|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Prend en charge la `SCC_CHECKOUT_LOCALVER` option des extractions.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Prend en charge le [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Prend en charge le [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Prend en charge la recherche de répertoires supplémentaires.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Prend en charge l’énumération des modifications apportées au fichier.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Prend en charge les [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Prend en charge les [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Prend en charge l’appel de SccQueryInfo sur plusieurs threads.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Prend en charge la fonction SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Peut supprimer des fichiers extraits.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Renommer les fichiers extraits.|  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
