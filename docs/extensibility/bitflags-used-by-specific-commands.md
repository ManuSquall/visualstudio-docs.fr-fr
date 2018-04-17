---
title: Indicateurs de bits utilisés par des commandes spécifiques | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bc59c79e0f047cc7880332c4c23643ab2136c86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="bitflags-used-by-specific-commands"></a>Indicateurs de bits utilisés par des commandes spécifiques
Le comportement d’un nombre de fonctions dans l’API de plug-in de contrôle de Source peut être modifié en définissant un ou plusieurs bits à une valeur unique. Ces valeurs sont des indicateurs de bits. Les différents indicateurs de bits utilisées par l’API de plug-in de contrôle de Source sont décrits ici, regroupés par la fonction qui les utilise.  
  
## <a name="checked-out-flag"></a>Extrait d’indicateur  
 Cet indicateur peut être défini pour une le [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Conserver le fichier extrait.|  
  
## <a name="add-flags"></a>Ajouter des indicateurs  
 Ces indicateurs sont utilisés par le [SccAdd](../extensibility/sccadd-function.md).  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Le plug-in de contrôle de code source est censé détecter automatiquement si le fichier est binaire ou texte.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Est du type de fichier texte.|  
|`SCC_FILETYPE_BINARY`|0 x 04|Type de fichier est binaire. **Remarque :** `SCC_FILETYPE_TEXT` et `SCC_FILETYPE_BINARY` les indicateurs sont mutuellement exclusifs.   Définir un seul ou aucune des deux.|  
|`SCC_ADD_STORELATEST`|0 x 02|Conserver la dernière version uniquement (aucune deltas).|  
  
## <a name="diff-flags"></a>Indicateurs de comparaison  
 Le [SccDiff](../extensibility/sccdiff-function.md) utilise ces indicateurs pour définir l’étendue d’une opération de comparaison. Le `SCC_DIFF_QD_xxx` les indicateurs sont mutuellement exclusifs. Si l’un d’eux est spécifié, aucun retour visuel n’est accordée. Dans une « comparaison rapide » (QD), le plug-in ne détermine pas comment le fichier est différent, uniquement s’il est différent. Si aucun de ces indicateurs sont spécifiés, qu'une « comparaison visual » est effectuée ; différences entre les fichiers détaillées sont calculées et affichées. Si le QD demandée n’est pas pris en charge, le plug-in se déplace sur le meilleur suivant. Par exemple, si l’IDE demande une somme de contrôle, et le plug-in ne prend pas en charge il, le plug-in n’un contenu intégral-Vérifiez (toujours beaucoup plus rapidement qu’un affichage visuel).  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0 x 0002|Ignorer les différences de casse.|  
|`SCC_DIFF_IGNORESPACE`|0 x 0004|Ignorer les différences d’espace blanc. **Remarque :** le `SCC_DIFF_IGNORECASE` et `SCC_DIFF_IGNORESPACE` les indicateurs sont des indicateurs de bits facultatif.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD en comparant le contenu du fichier.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD par la somme de contrôle.|  
|`SCC_DIFF_QD_TIME`|0 x 0040|QD par le cachet de date/heure de fichier.|  
|`SCC_DIFF_QUICK_DIFF`|0 x 0070|Il s’agit d’un masque utilisé pour vérifier tous les indicateurs de QD bits. Il ne doit pas être passé à une fonction ; les trois indicateurs de bits QD s’excluent mutuellement. QD ne signifie toujours aucun affichage de l’interface utilisateur.|  
  
## <a name="populatelist-flag"></a>Indicateur de PopulateList  
 Cet indicateur est utilisé par le [SccPopulateList](../extensibility/sccpopulatelist-function.md) dans le `fOptions` paramètre.  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|L’IDE est le passage d’annuaires, pas les fichiers.|  
  
## <a name="populatedirlist-flags"></a>Indicateurs de PopulateDirList  
 Ces indicateurs sont utilisés par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) dans le `fOptions` paramètre.  
  
|Valeur de l’option|Value|Description|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examinez un seul niveau de répertoires pour les répertoires (il s’agit de la valeur par défaut).|  
|SCC_PDL_RECURSIVE|0 x 0001|Récursive examiner tous les répertoires sous chaque répertoire donné.|  
|SCC_PDL_INCLUDEFILES|0 x 0002|Inclure les noms de fichiers dans le processus d’examen.|  
  
## <a name="openproject-flags"></a>Indicateurs de OpenProject  
 Ces indicateurs sont utilisés par le [SccOpenProject](../extensibility/sccopenproject-function.md) dans le `dwFlags` paramètre.  
  
|Valeur de l’option|Value|Description|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Si le projet n’existe pas dans le contrôle de code source, créez-le. Si cet indicateur n’est pas défini, inviter l’utilisateur pour le projet à créer (à moins que `SCC_OP_SILENTOPEN` indicateur est spécifié).|  
|SCC_OP_SILENTOPEN|0x00000002L|Ne pas demander à l’utilisateur de créer un projet. retourner simplement `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Obtenir les indicateurs  
 Ces indicateurs sont utilisés par le [SccGet](../extensibility/sccget-function.md) et [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|L’IDE est en passant des répertoires, pas les fichiers : obtenir tous les fichiers dans ces répertoires.|  
|`SCC_GET_RECURSIVE`|0x00000002L|L’IDE est le passage d’annuaires : obtenir ces répertoires et tous ses sous-répertoires.|  
  
## <a name="noption-values"></a>Valeurs nOption  
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `nOption` paramètre.  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Définir le statut de la file d’attente de l’événement.|  
|`SCC_OPT_USERDATA`|0x00000002L|Spécifier les données utilisateur pour `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L’IDE peut gérer Annuler|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Définissez un rappel pour les modifications de noms.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Désactiver l’extraction de l’interface utilisateur du plug-in du contrôle source et ne définissez pas de répertoire de travail.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Ajouter à partir du système de contrôle de code source pour spécifier un répertoire de travail. Essayez de partager dans le projet associé, s’il s’agit d’un descendant direct.|  
  
## <a name="dwval-bitflags"></a>dwVal indicateurs de bits  
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `dwVal` paramètre.  
  
|Indicateur|Valeur|Description|Utilisé par `nOption` valeur|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Interrompt l’activité de file d’attente d’événements.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Active la journalisation de file d’attente des événements.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Par défaut) N’a aucun mode Annuler ; plug-in doit fournir si vous le souhaitez.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE gère les annuler.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Par défaut) OK à extraire à partir de l’interface utilisateur de plug-in ; répertoire de travail est défini.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Aucun plug-in extraction de l’interface utilisateur, aucun répertoire de travail.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)