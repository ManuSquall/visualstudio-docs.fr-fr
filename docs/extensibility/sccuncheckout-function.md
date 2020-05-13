---
title: Fonction SccUncheckout (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700245"
---
# <a name="sccuncheckout-function"></a>Fonction SccUncheckout
Cette fonction annule une opération de caisse précédente, rétablissant ainsi le contenu du fichier ou des fichiers sélectionnés à l’état avant la caisse. Toutes les modifications apportées au fichier depuis la caisse sont perdues.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
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

[dans] Array de noms de chemin local entièrement qualifiés de fichiers pour lesquels annuler une caisse.

 fOptions

[dans] Drapeaux de commandement (non utilisés).

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La caisse annuler a été un succès.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique. La caisse non faite n’a pas réussi.|
|SCC_E_NOTCHECKEDOUT|L’utilisateur ne fait pas vérifier le fichier.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert à partir du contrôle des sources.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant l’achèvement.|

## <a name="remarks"></a>Notes
 Après cette opération, `SCC_STATUS_MODIFIED` les drapeaux et les `SCC_STATUS_CHECKEDOUT` drapeaux seront tous deux effacés pour les dossiers sur lesquels la caisse annuler a été effectuée.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
