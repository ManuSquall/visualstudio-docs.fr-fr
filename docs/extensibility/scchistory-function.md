---
description: Cette fonction affiche l’historique des fichiers spécifiés.
title: SccHistory fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902538"
---
# <a name="scchistory-function"></a>Fonction SccHistory
Cette fonction affiche l’historique des fichiers spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Paramètres
 `pvContext`

dans Structure de contexte du plug-in de contrôle de code source.

 `hWnd`

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 `nFiles`

dans Nombre de fichiers spécifiés dans le `lpFileName` tableau.

 `lpFileName`

dans Tableau de noms qualifiés complets de fichiers.

 `fOptions`

dans Indicateurs de commande (actuellement non utilisés).

 `pvOptions`

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’historique des versions a été obtenu avec succès.|
|SCC_I_RELOADFILE|Le système de contrôle de code source a en fait modifié le fichier sur le disque lors de la récupération de l’historique (par exemple, en obtenant une version antérieure), l’IDE doit donc recharger ce fichier.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique. Impossible d’obtenir l’historique des fichiers.|

## <a name="remarks"></a>Remarques
 Le plug-in de contrôle de code source peut afficher sa propre boîte de dialogue pour afficher l’historique de chaque fichier, en utilisant `hWnd` comme fenêtre parente. Vous pouvez également utiliser la fonction de rappel de sortie de texte facultative fournie à [SccOpenProject](../extensibility/sccopenproject-function.md) , si elle est prise en charge.

 Notez que dans certains cas, le fichier en cours d’examen peut changer pendant l’exécution de cet appel. Par exemple, la [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] commande History donne à l’utilisateur la possibilité d’obtenir une ancienne version du fichier. Dans ce cas, le plug-in de contrôle de code source retourne `SCC_I_RELOAD` pour avertir l’IDE qu’il doit recharger le fichier.

> [!NOTE]
> Si le plug-in de contrôle de code source ne prend pas en charge cette fonction pour un tableau de fichiers, seul l’historique des fichiers du premier fichier peut être affiché.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
