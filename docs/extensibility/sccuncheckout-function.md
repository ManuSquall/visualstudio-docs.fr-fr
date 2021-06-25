---
description: Cette fonction annule une opération d’extraction précédente, restaurant ainsi le contenu du ou des fichiers sélectionnés à l’état antérieur à l’extraction.
title: SccUncheckout fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a382a112b5a11acc36c52735c949ebef71052ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904085"
---
# <a name="sccuncheckout-function"></a>Fonction SccUncheckout
Cette fonction annule une opération d’extraction précédente, restaurant ainsi le contenu du ou des fichiers sélectionnés à l’état antérieur à l’extraction. Toutes les modifications apportées au fichier depuis l’extraction sont perdues.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms de chemins d’accès locaux complets des fichiers pour lesquels annuler une extraction.

 fOptions

dans Indicateurs de commande (non utilisés).

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’extraction de l’annulation a réussi.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous le contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique. Échec de l’extraction de l’annulation.|
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas le fichier extrait.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert à partir du contrôle de code source.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|

## <a name="remarks"></a>Remarques
 Après cette opération, les `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` indicateurs et seront tous deux désactivés pour les fichiers sur lesquels l’extraction d’annulation a été effectuée.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
