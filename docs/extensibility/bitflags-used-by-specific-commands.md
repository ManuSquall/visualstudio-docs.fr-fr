---
title: Indicateurs utilisé par des commandes spécifiques | Microsoft Docs
description: En savoir plus sur les indicateurs utilisés par l’API de plug-in de contrôle de code source, organisés par la fonction qui les utilise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be5915d96b574336d7091239275a2aaef456a7f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899365"
---
# <a name="bitflags-used-by-specific-commands"></a>Indicateurs utilisé par des commandes spécifiques
Le comportement d’un certain nombre de fonctions dans l’API de plug-in de contrôle de code source peut être modifié en définissant un ou plusieurs bits dans une valeur unique. Ces valeurs sont appelées indicateurs. Les différents indicateurs utilisés par l’API de plug-in de contrôle de code source sont détaillés ici, regroupés par la fonction qui les utilise.

## <a name="checked-out-flag"></a>Indicateur d’extraction
 Cet indicateur peut être défini pour [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Conservez le fichier extrait.|

## <a name="add-flags"></a>Ajouter des indicateurs
 Ces indicateurs sont utilisés par [SccAdd](../extensibility/sccadd-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Le plug-in de contrôle de code source est supposé détecter automatiquement si le fichier est du texte ou binaire.|
|`SCC_FILETYPE_TEXT`|0x01|Le type de fichier est texte.|
|`SCC_FILETYPE_BINARY`|0x04|Le type de fichier est binaire. **Remarque :** `SCC_FILETYPE_TEXT` les `SCC_FILETYPE_BINARY` indicateurs et s’excluent mutuellement.   Définissez exactement une ou aucune des deux.|
|`SCC_ADD_STORELATEST`|0x02|Stocker la dernière version uniquement (aucun Delta).|

## <a name="diff-flags"></a>Indicateurs diff
 Le [SccDiff](../extensibility/sccdiff-function.md) utilise ces indicateurs pour définir la portée d’une opération diff. Les `SCC_DIFF_QD_xxx` indicateurs s’excluent mutuellement. Si l’une d’entre elles est spécifiée, aucun commentaire visuel ne doit être donné. Dans un « diff. rapide » (QD), le plug-in ne détermine pas la manière dont le fichier est différent, mais uniquement s’il est différent. Si aucun de ces indicateurs n’est spécifié, un « diff visuel » est effectué ; les différences de fichiers détaillées sont calculées et affichées. Si le QD demandé n’est pas pris en charge, le plug-in est déplacé vers le suivant le plus approprié. Par exemple, si l’IDE demande une somme de contrôle et que le plug-in ne le prend pas en charge, le plug-in effectue un contrôle de contenu complet (toujours beaucoup plus rapide qu’un affichage visuel).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorer les différences de casse.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorer les différences d’espace blanc. **Remarque :**  Les `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` indicateurs et sont des indicateurs facultatifs.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD en comparant tout le contenu du fichier.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD par somme de contrôle.|
|`SCC_DIFF_QD_TIME`|0x0040|QD par horodatage de fichier date/heure.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Il s’agit d’un masque utilisé pour vérifier tous les indicateurs QD. Elle ne doit pas être passée dans une fonction. les trois indicateurs QD s’excluent mutuellement. QD signifie toujours aucun affichage de l’interface utilisateur.|

## <a name="populatelist-flag"></a>Indicateur PopulateList
 Cet indicateur est utilisé par [SccPopulateList](../extensibility/sccpopulatelist-function.md) dans le `fOptions` paramètre.

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|L’IDE passe des répertoires, pas des fichiers.|

## <a name="populatedirlist-flags"></a>Indicateurs PopulateDirList
 Ces indicateurs sont utilisés par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) dans le `fOptions` paramètre.

|Valeur d’option|Valeur|Description|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examinez un seul niveau de répertoires pour les répertoires (il s’agit de la valeur par défaut).|
|SCC_PDL_RECURSIVE|0x0001|Examinez de manière récursive tous les répertoires sous chaque répertoire donné.|
|SCC_PDL_INCLUDEFILES|0x0002|Incluez les noms de fichiers dans le processus d’examen.|

## <a name="openproject-flags"></a>Indicateurs OpenProject
 Ces indicateurs sont utilisés par le [SccOpenProject](../extensibility/sccopenproject-function.md) dans le `dwFlags` paramètre.

|Valeur d’option|Valeur|Description|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Si le projet n’existe pas dans le contrôle de code source, créez-le. Si cet indicateur n’est pas défini, invite l’utilisateur à créer un projet (sauf si l' `SCC_OP_SILENTOPEN` indicateur est spécifié).|
|SCC_OP_SILENTOPEN|0x00000002L|Ne pas demander à l’utilisateur de créer un projet ; renvoyez simplement `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Afficher les indicateurs
 Ces indicateurs sont utilisés par [SccGet](../extensibility/sccget-function.md) et [SccCheckout](../extensibility/scccheckout-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|L’IDE passe des répertoires, et non des fichiers : récupère tous les fichiers dans ces répertoires.|
|`SCC_GET_RECURSIVE`|0x00000002L|L’environnement de développement intégré (IDE) passe des répertoires : obtient ces répertoires et tous leurs sous-répertoires.|

## <a name="noption-values"></a>valeurs nOption
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `nOption` paramètre.

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Définissez l’état de la file d’attente d’événements.|
|`SCC_OPT_USERDATA`|0x00000002L|Spécifiez les données utilisateur pour `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L’IDE peut gérer l’annulation.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Définissez un rappel pour les modifications de nom.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Désactiver l’extraction de l’interface utilisateur du plug-in de contrôle de code source et ne pas définir le répertoire de travail.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Ajoutez à partir du système de contrôle de code source pour spécifier un répertoire de travail. Essayez de partager dans le projet associé s’il s’agit d’un descendant direct.|

## <a name="dwval-bitflags"></a>dwVal indicateurs
 Ces indicateurs sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `dwVal` paramètre.

|Indicateur|Valeur|Description|Utilisé par `nOption` valeur|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Interrompt l’activité de la file d’attente des événements.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Active la journalisation des files d’attente d’événements.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Valeurs N’a pas de mode annulation ; le plug-in doit fournir si vous le souhaitez.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|L’IDE gère l’annulation.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Valeurs OK pour extraire de l’interface utilisateur du plug-in ; le répertoire de travail est défini.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Aucune extraction de l’interface utilisateur du plug-in, pas de répertoire de travail.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
