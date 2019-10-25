---
title: SccRename fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b2928653507b670160c72ca3ce09a0227a4170
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720764"
---
# <a name="sccrename-function"></a>Fonction SccRename
Cette fonction renomme un fichier dans le système de contrôle de code source.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

dans Nom de fichier complet du fichier renommé.

 lpNewName

dans Nouveau nom complet. Si le chemin d’accès au répertoire est différent, le fichier a été déplacé d’un sous-répertoire à un autre.

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération de changement de nom s’est terminée avec succès.|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous le contrôle de code source.|
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’a pas pu être créé dans le cadre du processus de changement de nom.|
|SCC_E_OPNOTPERFORMED|L’opération n’a pas été effectuée.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Cette fonction peut être utilisée pour renommer un fichier ou le déplacer d’un emplacement à un autre dans le système de contrôle de code source. Le plug-in de contrôle de code source ne doit pas tenter d’accéder au fichier sur le disque. Il incombe à l’IDE de renommer le fichier local.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)