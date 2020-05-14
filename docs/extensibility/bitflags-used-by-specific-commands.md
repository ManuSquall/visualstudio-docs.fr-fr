---
title: Bitflags utilisés par des commandes spécifiques ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740013"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags utilisés par des commandes spécifiques
Le comportement d’un certain nombre de fonctions dans l’API de contrôle source rechargeable peut être modifié en définissant un ou plusieurs bits en une seule valeur. Ces valeurs sont connues sous le nom de bitflags. Les différents bitflags utilisés par l’API de contrôle source sont détaillés ici, regroupés par la fonction qui les utilise.

## <a name="checked-out-flag"></a>Indicateur vérifié
 Ce drapeau peut être défini pour le [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Gardez le fichier vérifié.|

## <a name="add-flags"></a>Ajouter des drapeaux
 Ces drapeaux sont utilisés par le [SccAdd](../extensibility/sccadd-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Le plug-in de contrôle source devrait détecter automatiquement si le fichier est texte ou binaire.|
|`SCC_FILETYPE_TEXT`|0x01|Le type de fichier est le texte.|
|`SCC_FILETYPE_BINARY`|0x04|Le type de fichier est binaire. **Note:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` et les drapeaux sont mutuellement exclusifs.   Définissez exactement un ou l’un ni l’autre.|
|`SCC_ADD_STORELATEST`|0x02|Stockez la dernière version uniquement (pas de deltas).|

## <a name="diff-flags"></a>Drapeaux Diff
 Le [SccDiff](../extensibility/sccdiff-function.md) utilise ces drapeaux pour définir la portée d’une opération diff. Les `SCC_DIFF_QD_xxx` drapeaux s’excluent mutuellement. Si l’un d’eux est spécifié, alors aucune rétroaction visuelle ne doit être donnée. Dans un "diff rapide" (QD), le plug-in ne détermine pas comment le fichier est différent, seulement si elle est différente. Si aucun de ces drapeaux n’est spécifié, un « diff visuel » est fait ; les différences détaillées de fichiers sont calculées et affichées. Si le QD demandé n’est pas pris en charge, le plug-in passe au meilleur suivant. Par exemple, si l’IDE demande un checkum, et le plug-in ne le prend pas en charge, le plug-in fait une vérification complète du contenu (encore beaucoup plus rapide qu’un affichage visuel).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorer les différences de cas.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorer les différences d’espace blanc. **Note:**  Les `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` drapeaux et les drapeaux sont des bitflags optionnels.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD en comparant le contenu entier du fichier.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD par checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|QD par date de fichier / timbre d’heure.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Il s’agit d’un masque utilisé pour vérifier tous les bitflags QD. Il ne doit pas être passé dans une fonction; les trois bitflags QD s’excluent mutuellement. QD signifie toujours pas d’affichage de l’interface utilisateur.|

## <a name="populatelist-flag"></a>Indicateur De PopulateList
 Ce drapeau est utilisé par le [SccPopulateList](../extensibility/sccpopulatelist-function.md) dans le `fOptions` paramètre.

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|L’IDE passe des répertoires, pas des fichiers.|

## <a name="populatedirlist-flags"></a>Drapeaux PopulateDirList
 Ces drapeaux sont utilisés par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) dans le `fOptions` paramètre.

|Valeur d’option|Valeur|Description|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examinez un seul niveau d’annuaires pour les répertoires (c’est la valeur par défaut).|
|SCC_PDL_RECURSIVE|0x0001|Examinez de façon récursive tous les répertoires sous chaque répertoire donné.|
|SCC_PDL_INCLUDEFILES|0x0002|Inclure les noms de fichiers dans le processus d’examen.|

## <a name="openproject-flags"></a>Drapeaux OpenProject
 Ces drapeaux sont utilisés par le [SccOpenProject](../extensibility/sccopenproject-function.md) dans le `dwFlags` paramètre.

|Valeur d’option|Valeur|Description|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Si le projet n’existe pas dans le contrôle source, créez-le. Si ce drapeau n’est pas défini, `SCC_OP_SILENTOPEN` invitez l’utilisateur pour le projet à créer (sauf indication du drapeau).|
|SCC_OP_SILENTOPEN|0x00000002L|N’invitez pas l’utilisateur à créer un projet; il `SCC_E_UNKNOWNPROJECT`suffit de revenir .|

## <a name="get-flags"></a>Obtenez des drapeaux
 Ces drapeaux sont utilisés par le [SccGet](../extensibility/sccget-function.md) et le [SccCheckout](../extensibility/scccheckout-function.md).

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|L’IDE passe des répertoires, pas des fichiers: Obtenez tous les fichiers dans ces répertoires.|
|`SCC_GET_RECURSIVE`|0x00000002L|L’IDE passe des répertoires: Obtenir ces répertoires et tous leurs sous-directeurs.|

## <a name="noption-values"></a>n Valeurs d’opposition
 Ces drapeaux sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `nOption` paramètre.

|Indicateur|Valeur|Description|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Définissez l’état de la file d’attente de l’événement.|
|`SCC_OPT_USERDATA`|0x00000002L|Spécifier `SCC_OPT_NAMECHANGEPFN`les données utilisateur pour .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L’IDE peut gérer l’annulation.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Réglez un rappel pour les modifications de nom.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Désactiver la caisse de contrôle des sources UI et ne pas définir répertoire de travail.|
|`SCC_OPT_SHARESUBPROJ`|0x0000006L|Ajouter à partir du système de contrôle source pour spécifier un répertoire de travail. Essayez de partager dans le projet associé s’il s’agit d’un descendant direct.|

## <a name="dwval-bitflags"></a>bitflags dwVal
 Ces drapeaux sont utilisés par le [SccSetOption](../extensibility/sccsetoption-function.md) dans le `dwVal` paramètre.

|Indicateur|Valeur|Description|Utilisé `nOption` par valeur|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspend l’activité de file d’attente d’événements.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Permet l’enregistrement des files d’attente d’événements.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Par défaut) N’a pas de mode d’annulation; plug-in doit fournir si désiré.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Les poignées IDE annulent.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Par défaut) OK pour vérifier à partir de plug-in UI; répertoire de travail est fixé.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Pas de caisse d’assurance-chômage rechargeable, pas d’annuaire de travail.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
