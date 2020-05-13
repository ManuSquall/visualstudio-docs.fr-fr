---
title: Fonction SccRename (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700427"
---
# <a name="sccrename-function"></a>Fonction SccRename
Cette fonction renomme un fichier dans le système de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

[dans] Le nom de fichier entièrement qualifié du fichier en cours de renom.

 lpNewName

[in] Nom qualifié complet du nouveau nom. Si le parcours d’annuaire est différent, alors le fichier est passé d’une sous-direction à l’autre.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération de changement de nom s’est terminée avec succès.|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle source.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’a pas pu être créé dans le cadre du processus de changement de nom.|
|SCC_E_OPNOTPERFORMED|L’opération n’a pas été effectuée.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Cette fonction peut être utilisée pour renommer un fichier ou le déplacer d’un endroit à l’autre dans le système de contrôle source. Le plug-in de contrôle source ne doit pas tenter d’accéder au fichier sur disque. Il incombe à l’IDE de renommer le fichier local.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
