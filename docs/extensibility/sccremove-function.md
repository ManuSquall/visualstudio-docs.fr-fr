---
title: SccRemove fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b0691c3f58ad859051f0018e7b32a5a4e087da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836707"
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

dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

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

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La suppression a réussi.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ISCHECKEDOUT|Impossible de supprimer un fichier parce qu’il est actuellement extrait par un utilisateur.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; le fichier n’a pas été supprimé.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|

## <a name="remarks"></a>Remarques
 Cette fonction supprime les fichiers du système de contrôle de code source, mais ne les supprime pas du disque dur local de l’utilisateur.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
