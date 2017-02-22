---
title: "Indicateurs de bits utilis&#233;s par des commandes sp&#233;cifiques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-ins, les indicateurs de bits utilisés par les commandes spécifiques de contrôle de code source"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Indicateurs de bits utilis&#233;s par des commandes sp&#233;cifiques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le comportement d'un nombre de fonctions de l'API de plug\-in de contrôle Source peut être modifié en définissant un ou plusieurs bits dans une valeur unique. Ces valeurs sont des indicateurs de bits. Les différents indicateurs de bits utilisés par l'API de plug\-in de contrôle de Source sont détaillées ici, regroupées par la fonction qui les utilise.  
  
## Extrait d'indicateur  
 Cet indicateur peut être défini pour le [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0 x 1000|Conserver le fichier extrait.|  
  
## Ajouter des indicateurs  
 Ces indicateurs sont utilisés par le [SccAdd](../extensibility/sccadd-function.md).  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_FILETYPE_AUTO`|0 x 00|Le plug\-in de contrôle de code source est prévu pour détecter automatiquement si le fichier est binaire ou texte.|  
|`SCC_FILETYPE_TEXT`|0 x 01|Type de fichier est texte.|  
|`SCC_FILETYPE_BINARY`|0 x 04|Type de fichier est binaire. **Note:**  `SCC_FILETYPE_TEXT` et `SCC_FILETYPE_BINARY` indicateurs sont mutuellement exclusifs. Définissez une ou aucune des deux.|  
|`SCC_ADD_STORELATEST`|0 x 02|Conserver la dernière version uniquement \(aucune deltas\).|  
  
## Indicateurs de comparaison  
 Le [SccDiff](../extensibility/sccdiff-function.md) utilise ces indicateurs pour définir l'étendue d'une opération de comparaison. Le `SCC_DIFF_QD_xxx` indicateurs sont mutuellement exclusifs. Si l'un d'eux est spécifié, aucun signal visuel n'est accordée. Dans une « comparaison rapide » \(QD\), le plug\-in ne détermine pas comment le fichier est différent, uniquement s'il est différent. Si aucun de ces indicateurs sont spécifiés, qu'un « visuel diff » est effectuée ; différences entre les fichiers détaillées sont calculées et affichées. Si le QD demandée n'est pas pris en charge, le plug\-in se déplace à la suivante meilleures. Par exemple, si l'IDE demande une somme de contrôle et le plug\-in ne prend pas en charge cela, le plug\-in ne contenu d'un intégral Vérifiez \(toujours beaucoup plus rapidement qu'un affichage visuel\).  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0 x 0002|Ignorer les différences de casse.|  
|`SCC_DIFF_IGNORESPACE`|0 x 0004|Ignorer les différences d'espace blanc. **Note:**  Le `SCC_DIFF_IGNORECASE` et `SCC_DIFF_IGNORESPACE` les indicateurs sont des indicateurs de bits facultatif.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD en comparant le contenu du fichier.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD par la somme de contrôle.|  
|`SCC_DIFF_QD_TIME`|0 x 0040|QD par horodatage date\/heure de fichier.|  
|`SCC_DIFF_QUICK_DIFF`|0 x 0070|Il s'agit d'un masque utilisé pour vérifier tous les indicateurs de bits QD. Il ne doit pas être passé dans une fonction ; les trois indicateurs de bits QD s'excluent mutuellement. QD ne signifie toujours aucun affichage de l'interface utilisateur.|  
  
## Indicateur de PopulateList  
 Cet indicateur est utilisé par le [SccPopulateList](../extensibility/sccpopulatelist-function.md) dans le `fOptions` paramètre.  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|L'IDE est en passant des répertoires, pas les fichiers.|  
  
## Indicateurs de PopulateDirList  
 Ces indicateurs sont utilisés par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) dans le `fOptions` paramètre.  
  
|Valeur de l'option|Valeur|Description|  
|------------------------|------------|-----------------|  
|SCC\_PDL\_ONELEVEL|0x0000|Vérifiez qu'un seul niveau de répertoires pour les répertoires \(c'est la valeur par défaut\).|  
|SCC\_PDL\_RECURSIVE|0 x 0001|Récursivement examiner tous les répertoires sous chaque répertoire donné.|  
|SCC\_PDL\_INCLUDEFILES|0 x 0002|Inclure les noms de fichiers dans le processus d'examen.|  
  
## Indicateurs de OpenProject  
 Ces indicateurs sont utilisés par le [SccOpenProject](../extensibility/sccopenproject-function.md) dans le `dwFlags` paramètre.  
  
|Valeur de l'option|Valeur|Description|  
|------------------------|------------|-----------------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|Si le projet n'existe pas dans le contrôle de code source, créez\-le. Si cet indicateur n'est pas défini, inviter l'utilisateur pour le projet à créer \(à moins que `SCC_OP_SILENTOPEN` indicateur est spécifié\).|  
|SCC\_OP\_SILENTOPEN|0x00000002L|Ne demande pas l'utilisateur de créer un projet. retourner simplement `SCC_E_UNKNOWNPROJECT`.|  
  
## Obtenir les indicateurs  
 Ces indicateurs sont utilisés par le [SccGet](../extensibility/sccget-function.md) et le [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|L'IDE est en passant des répertoires, pas les fichiers : obtenir tous les fichiers dans ces répertoires.|  
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE est en passant des répertoires : obtenir ces répertoires et tous ses sous\-répertoires.|  
  
## Valeurs nOption  
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `nOption` paramètre.  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Définir l'état de la file d'attente d'événements.|  
|`SCC_OPT_USERDATA`|0x00000002L|Spécifier les données utilisateur `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE peut gérer l'annulation|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Définir un rappel pour les changements de nom.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Désactiver l'extraction de l'interface utilisateur du plug\-in du contrôle source et ne définissez pas de répertoire de travail.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Ajouter à partir du système de contrôle source permet de spécifier un répertoire de travail. Essayez de partager dans le projet associé, s'il s'agit d'un descendant direct.|  
  
## dwVal indicateurs de bits  
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `dwVal` paramètre.  
  
|Indicateur|Valeur|Description|Utilisé par `nOption` valeur|  
|----------------|------------|-----------------|----------------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Interrompt l'activité de file d'attente d'événements.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Permet l'enregistrement de file d'attente des événements.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|\(Par défaut\) N'a aucun mode annulation ; plug\-in doit fournir si vous le souhaitez.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE gère les annuler.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|\(Par défaut\) Cliquez sur OK pour extraire de l'interface utilisateur du plug\-in ; répertoire de travail est défini.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Aucun plug\-in extraction de l'interface utilisateur, aucun répertoire de travail.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)