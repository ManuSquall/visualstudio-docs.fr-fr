---
title: Fonction SccRename | Microsoft Docs
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
ms.openlocfilehash: 1329f847f7f961bf4c792cbdf7f40f8f04b1694c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338727"
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
 pvContext

[in] La structure de contexte de plug-in de contrôle de source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 lpFileName

[in] Le nom de fichier qualifié complet du fichier qui est renommé.

 lpNewName

[in] Nouveau nom qualifié complet. Si le chemin du répertoire est différent, le fichier a été déplacé à partir d’un sous-répertoire à un autre.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|L’opération de changement de nom s’est terminée correctement.|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle de code source.|
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’a pas pu être créé dans le cadre du processus de changement de nom.|
|SCC_E_OPNOTPERFORMED|L’opération n’a pas été effectuée.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Cette fonction peut être utilisée pour renommer un fichier ou le déplacer d’un emplacement vers un autre dans le système de contrôle de source. Le plug-in de contrôle de code source ne devez pas essayer d’accéder au fichier sur le disque. Il incombe de l’IDE pour renommer le fichier local.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)