---
description: Cette fonction affiche les différences entre le répertoire local actuel sur le disque client et le projet correspondant sous contrôle de code source.
title: SccDirDiff fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904641"
---
# <a name="sccdirdiff-function"></a>SccDirDiff fonction)
Cette fonction affiche les différences entre le répertoire local actuel sur le disque client et le projet correspondant sous contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpDirName

dans Chemin d’accès complet au répertoire local pour lequel une différence visuelle est affichée.

 dwFlags

dans Indicateurs de commande (consultez la section Notes).

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le répertoire sur le disque est le même que le projet dans le contrôle de code source.|
|SCC_I_FILESDIFFER|Le répertoire sur le disque est différent du projet dans le contrôle de code source.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTCONTROLLED|Le répertoire n’est pas sous le contrôle de code source.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|
|SCC_E_FILENOTEXIST|Le répertoire local est introuvable.|

## <a name="remarks"></a>Remarques
 Cette fonction est utilisée pour indiquer au plug-in de contrôle de code source qu’il doit afficher à l’utilisateur une liste des modifications apportées à un répertoire spécifié. Le plug-in ouvre sa propre fenêtre, dans un format de son choix, pour afficher les différences entre l’annuaire de l’utilisateur sur le disque et le projet correspondant sous contrôle de version.

 Si un plug-in prend en charge la comparaison des répertoires, il doit prendre en charge la comparaison des répertoires sur la base du nom de fichier, même si les options de différence rapide ne sont pas prises en charge.

|`dwFlags`|Interprétation|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparaison ne respectant pas la casse (peut être utilisé pour une comparaison rapide ou un visuel).|
|SCC_DIFF_IGNORESPACE|Ignore les espaces blancs (peut être utilisé pour une comparaison rapide ou un visuel).|
|SCC_DIFF_QD_CONTENTS|S’il est pris en charge par le plug-in de contrôle de code source, compare silencieusement le répertoire, octet par octet.|
|SCC_DIFF_QD_CHECKSUM|S’il est pris en charge par le plug-in, compare silencieusement le répertoire par le biais d’une somme de contrôle, ou, s’il n’est pas pris en charge, revient à SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|S’il est pris en charge par le plug-in, compare silencieusement le répertoire à l’aide de son horodateur, ou, s’il n’est pas pris en charge, revient sur SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Cette fonction utilise les mêmes indicateurs de commande que le [SccDiff](../extensibility/sccdiff-function.md). Toutefois, un plug-in de contrôle de code source peut choisir de ne pas prendre en charge l’opération « comparaison rapide » pour les répertoires.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
