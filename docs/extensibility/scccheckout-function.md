---
title: Fonction SccCheckout (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701107"
---
# <a name="scccheckout-function"></a>Fonction SccCheckout
Compte tenu d’une liste de noms de fichiers entièrement qualifiés, cette fonction les vérifie à la commande locale. Le commentaire s’applique à tous les fichiers en cours de vérification. L’argument du `null` commentaire peut être une chaîne.

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
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers sélectionnés pour être vérifiés.

 lpFileNames

[dans] Array de noms de chemin local entièrement qualifiés de fichiers à vérifier.

 lpComment

[dans] Commentaire à appliquer à chacun des fichiers sélectionnés en cours de vérification.

 fOptions

[dans] Drapeaux de commandement (voir [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le départ a été un succès.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique. Le fichier n’a pas été vérifié.|
|SCC_E_ALREADYCHECKEDOUT|L’utilisateur a déjà le fichier vérifié.|
|SCC_E_FILEISLOCKED|Le fichier est verrouillé, interdisant la création de nouvelles versions.|
|SCC_E_FILEOUTEXCLUSIVE|Un autre utilisateur a fait une caisse exclusive sur ce fichier.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant l’achèvement.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
