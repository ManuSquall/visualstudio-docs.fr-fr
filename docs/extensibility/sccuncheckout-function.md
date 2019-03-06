---
title: Fonction SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6362025f63e4e4f470a7fe107365a59ef99e1e17
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717414"
---
# <a name="sccuncheckout-function"></a>Fonction SccUncheckout
Cette fonction annule une opération d’extraction précédente, restaurant ainsi le contenu de l’ou les fichiers sélectionnés à l’état précédant l’extraction. Toutes les modifications apportées au fichier depuis l’extraction sont perdues.

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

[in] La structure de contexte de plug-in de contrôle de source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 nFiles

[in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

[in] Tableau des noms de chemin d’accès local complet des fichiers pour lequel annuler une extraction.

 fOptions

[in] Indicateurs de commande (non utilisés).

 pvOptions

[in] Options spécifiques au plug-in de contrôle source.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Annulation de l’extraction a réussi.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Annuler extraction n’a pas réussi.|
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas extrait le fichier.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert à partir du contrôle de code source.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|

## <a name="remarks"></a>Notes
 Après cette opération, le `SCC_STATUS_CHECKEDOUT` et `SCC_STATUS_MODIFIED` indicateurs seront désactivées pour les fichiers sur lequel l’annulation de l’extraction a été effectuée.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)