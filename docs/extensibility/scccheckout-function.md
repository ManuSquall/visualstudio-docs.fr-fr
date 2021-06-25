---
description: À partir d’une liste de noms de fichiers complets, cette fonction les extrait sur le lecteur local.
title: SccCheckout fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904719"
---
# <a name="scccheckout-function"></a>SccCheckout fonction)
À partir d’une liste de noms de fichiers complets, cette fonction les extrait sur le lecteur local. Le commentaire s’applique à tous les fichiers en cours d’extraction. L’argument de commentaire peut être une `null` chaîne.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers sélectionnés à extraire.

 lpFileNames

dans Tableau de noms de chemins d’accès locaux complets des fichiers à extraire.

 lpComment

dans Commentaire à appliquer à chacun des fichiers sélectionnés en cours d’extraction.

 fOptions

dans Indicateurs de commande (consultez [indicateurs utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’extraction a réussi.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous le contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique. Le fichier n’a pas été extrait.|
|SCC_E_ALREADYCHECKEDOUT|Le fichier est déjà extrait par l’utilisateur.|
|SCC_E_FILEISLOCKED|Le fichier est verrouillé, ce qui interdit la création de nouvelles versions.|
|SCC_E_FILEOUTEXCLUSIVE|Un autre utilisateur a effectué une extraction en mode exclusif sur ce fichier.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs utilisé par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
