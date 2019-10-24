---
title: SccRemove fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ff7299868b96aedb7cc096b4e939a0f8015aeb8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720774"
---
# <a name="sccremove-function"></a>Fonction SccRemove
Cette fonction supprime les fichiers du système de contrôle de code source.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers spécifiés dans le tableau de `lpFileNames`.

 lpFileNames

dans Tableau de noms de chemins d’accès locaux complets des fichiers à supprimer.

 lpComment

dans Commentaire à appliquer à chaque fichier supprimé.

 fOptions

dans Indicateurs de commande (inutilisé).

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|La suppression a réussi.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ISCHECKEDOUT|Impossible de supprimer un fichier parce qu’il est actuellement extrait par un utilisateur.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; le fichier n’a pas été supprimé.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|

## <a name="remarks"></a>Notes
 Cette fonction supprime les fichiers du système de contrôle de code source, mais ne les supprime pas du disque dur local de l’utilisateur.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)