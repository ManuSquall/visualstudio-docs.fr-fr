---
description: Cette fonction affiche (ou vérifie éventuellement uniquement) les différences entre le fichier actif (sur le disque local) et sa dernière version archivée dans le système de contrôle de code source.
title: SccDiff fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904654"
---
# <a name="sccdiff-function"></a>SccDiff fonction)
Cette fonction affiche (ou vérifie éventuellement uniquement) les différences entre le fichier actif (sur le disque local) et sa dernière version archivée dans le système de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

dans Nom de fichier pour lequel la différence est demandée.

 fOptions

dans Indicateurs de commande. Pour plus de détails, consultez la section Notes.

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La copie de travail et la version du serveur sont identiques.|
|SCC_I_FILESDIFFERS|La copie de travail diffère de la version sous contrôle de code source.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; la différence de fichier n’a pas été obtenue.|
|SCC_E_FILENOTEXIST|Le fichier local est introuvable.|

## <a name="remarks"></a>Remarques
 Cette fonction remplit deux fonctions différentes. Par défaut, il affiche la liste des modifications apportées à un fichier. Le plug-in de contrôle de code source ouvre sa propre fenêtre, dans le format qu’il choisit, pour afficher les différences entre le fichier de l’utilisateur sur le disque et la dernière version du fichier sous contrôle de code source.

 L’IDE peut également simplement avoir besoin de déterminer si un fichier a été modifié. Par exemple, l’IDE peut avoir besoin de déterminer s’il est possible d’extraire en toute sécurité un fichier sans en informer l’utilisateur. Dans ce cas, l’IDE passe l' `SCC_DIFF_CONTENTS` indicateur. Le plug-in de contrôle de code source doit vérifier le fichier sur le disque, octet par octet, par rapport au fichier sous contrôle de code source et retourner une valeur indiquant si les deux fichiers sont différents sans afficher d’éléments à l’utilisateur.

 Pour optimiser les performances, le plug-in de contrôle de code source peut utiliser une alternative basée sur une somme de contrôle ou un horodateur au lieu de la comparaison octet par octet appelée pour par `SCC_DIFF_CONTENTS` : ces formes de comparaison sont évidemment plus rapides mais moins fiables. Tous les systèmes de contrôle de code source ne peuvent pas prendre en charge ces méthodes de comparaison alternatives, et le plug-in peut avoir à revenir à une comparaison de contenu. Tous les plug-ins de contrôle de code source doivent, au minimum, prendre en charge une comparaison de contenu.

> [!NOTE]
> Les indicateurs de différence rapide s’excluent mutuellement. Il est possible de ne passer aucun indicateur, mais il n’est pas possible de passer simultanément plus d’un. `SCC_DIFF_QUICK_DIFF`, qui est un masque qui combine tous les indicateurs, peut être utilisé pour tester, mais il ne doit jamais être passé comme paramètre.

|`fOption`|Signification|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparaison qui ne respecte pas la casse (peut être utilisée pour une différence visuelle ou rapide).|
|SCC_DIFF_IGNORESPACE|Ignore les espaces blancs (peut être utilisé pour une différence visuelle ou rapide).|
|SCC_DIFF_QD_CONTENTS|Compare silencieusement le fichier, octet par octet.|
|SCC_DIFF_QD_CHECKSUM|Compare silencieusement le fichier à l’aide d’une somme de contrôle lorsqu’il est pris en charge. S’il n’est pas pris en charge, revient à une comparaison des contenus.|
|SCC_DIFF_QD_TIME|Compare silencieusement le fichier à l’aide de son horodateur lorsqu’il est pris en charge. S’il n’est pas pris en charge, revient à une comparaison des contenus.|

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
