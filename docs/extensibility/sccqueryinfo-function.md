---
title: Fonction SccQueryInfo (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700477"
---
# <a name="sccqueryinfo-function"></a>Fonction SccQueryInfo
Cette fonction obtient des informations d’état pour un ensemble de fichiers sélectionnés sous contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 nFiles

[dans] Nombre de fichiers `lpFileNames` spécifiés dans le `lpStatus` tableau et la longueur du tableau.

 lpFileNames

[dans] Un éventail de noms de fichiers à interroger.

 lpStatus

[dans, dehors] Un tableau dans lequel le plug-in de contrôle source renvoie les indicateurs d’état pour chaque fichier. Pour plus d’informations, voir [Code d’État du fichier](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La requête a été un succès.|
|SCC_E_ACCESSFAILURE|Il y avait un problème avec l’accès au système de contrôle source, probablement causé par des problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle source.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 S’il `lpFileName` s’agit d’une chaîne vide, il n’y a actuellement aucune information d’état à mettre à jour. Dans le cas contraire, c’est le nom complet du fichier pour lequel les informations sur l’état peuvent avoir changé.

 Le tableau de retour peut `SCC_STATUS_xxxx` être un peumask de bits. Pour plus d’informations, voir [Code d’État du fichier](../extensibility/file-status-code-enumerator.md). Un système de contrôle source peut ne pas prendre en charge tous les types de bits. Par exemple, `SCC_STATUS_OUTOFDATE` si ce n’est pas offert, le bit n’est tout simplement pas réglé.

 Lors de l’utilisation de cette `MSSCCI` fonction pour vérifier les fichiers, notez les exigences de statut suivantes :

- `SCC_STATUS_OUTBYUSER`est défini lorsque l’utilisateur actuel a vérifié le fichier.

- `SCC_STATUS_CHECKEDOUT`ne peut `SCC_STATUS_OUTBYUSER` pas être défini à moins d’être défini.

- `SCC_STATUS_CHECKEDOUT`n’est défini que lorsque le fichier est vérifié dans l’annuaire de travail désigné.

- Si le fichier est vérifié par l’utilisateur actuel dans un `SCC_STATUS_OUTBYUSER` répertoire autre `SCC_STATUS_CHECKEDOUT` que l’annuaire de travail, est défini mais ne l’est pas.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)
