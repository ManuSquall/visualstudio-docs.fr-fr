---
title: Fonction SccRemove (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700455"
---
# <a name="sccremove-function"></a>Fonction SccRemove
Cette fonction supprime les fichiers du système de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers `lpFileNames` spécifiés dans le tableau.

 lpFileNames

[dans] Array de noms de chemin local entièrement qualifiés des fichiers à supprimer.

 lpComment

[dans] Le commentaire à appliquer à chaque fichier supprimé.

 fOptions

[dans] Drapeaux de commandement (inutilisés).

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’enlèvement a été un succès.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle à la source ne prend pas en charge cette opération.|
|SCC_E_ISCHECKEDOUT|Impossible de supprimer un fichier parce qu’un utilisateur l’a actuellement vérifié.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique; n’a pas été supprimé.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant l’achèvement.|

## <a name="remarks"></a>Notes
 Cette fonction supprime les fichiers du système de contrôle source, mais ne les supprime pas du disque dur local de l’utilisateur.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
