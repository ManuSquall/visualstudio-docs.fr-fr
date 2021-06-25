---
description: Cette fonction met à jour une liste de fichiers pour une commande de contrôle de code source particulière et fournit l’état du contrôle de code source sur tous les fichiers donnés.
title: SccPopulateList fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902343"
---
# <a name="sccpopulatelist-function"></a>Fonction SccPopulateList
Cette fonction met à jour une liste de fichiers pour une commande de contrôle de code source particulière et fournit l’état du contrôle de code source sur tous les fichiers donnés.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 nLigne

dans Commande de contrôle de code source qui sera appliquée à tous les fichiers du `lpFileNames` tableau (consultez le [Code de commande](../extensibility/command-code-enumerator.md) pour obtenir la liste des commandes possibles).

 Nfichiers

dans Nombre de fichiers dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms de fichiers connus de l’IDE.

 pfnPopulate

dans Fonction de rappel de l’IDE à appeler pour ajouter et supprimer des fichiers (pour plus d’informations, consultez [POPLISTFUNC](../extensibility/poplistfunc.md) ).

 pvCallerData

dans Valeur qui doit être passée sans modification à la fonction de rappel.

 lpStatus

[in, out] Tableau pour que le plug-in de contrôle de code source retourne les indicateurs d’état de chaque fichier.

 fOptions

dans Indicateurs de commande (consultez la section « indicateur PopulateList » de [indicateurs utilisée par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour plus d’informations).

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Cette fonction examine la liste des fichiers pour déterminer son état actuel. Elle utilise la `pfnPopulate` fonction de rappel pour notifier l’appelant lorsqu’un fichier ne correspond pas aux critères de `nCommand` . Par exemple, si la commande est `SCC_COMMAND_CHECKIN` et qu’un fichier de la liste n’est pas extrait, le rappel est utilisé pour informer l’appelant. Parfois, le plug-in de contrôle de code source peut trouver d’autres fichiers qui peuvent faire partie de la commande et les ajouter. Cela permet, par exemple, à un utilisateur de Visual Basic d’extraire un fichier .bmp utilisé par son projet, mais qui n’apparaît pas dans le fichier de projet Visual Basic. Un utilisateur choisit la commande **obtenir** dans l’IDE. L’IDE affiche une liste de tous les fichiers qu’il estime que l’utilisateur peut obtenir, mais avant l’affichage de la liste, la `SccPopulateList` fonction est appelée pour s’assurer que la liste à afficher est à jour.

## <a name="example"></a>Exemple
 L’IDE génère une liste de fichiers que l’utilisateur peut obtenir. Avant d’afficher cette liste, elle appelle la `SccPopulateList` fonction, donnant au plug-in de contrôle de code source la possibilité d’ajouter et de supprimer des fichiers dans la liste. Le plug-in modifie la liste en appelant la fonction de rappel donnée (pour plus d’informations, consultez [POPLISTFUNC](../extensibility/poplistfunc.md) ).

 Le plug-in continue d’appeler la `pfnPopulate` fonction, qui ajoute et supprime des fichiers, jusqu’à ce qu’il soit terminé, puis retourne à partir de la `SccPopulateList` fonction. L’IDE peut ensuite afficher sa liste. Le `lpStatus` tableau représente tous les fichiers de la liste d’origine transmis par l’IDE. Le plug-in remplit l’état de tous ces fichiers en plus de l’utilisation de la fonction de rappel.

> [!NOTE]
> Un plug-in de contrôle de code source a toujours la possibilité de simplement retourner immédiatement à partir de cette fonction, en laissant la liste telle quelle. Si un plug-in implémente cette fonction, il peut l’indiquer en définissant l' `SCC_CAP_POPULATELIST` indicateur de bits des fonctionnalités dans le premier appel à [SccInitialize](../extensibility/sccinitialize-function.md). Par défaut, le plug-in doit toujours supposer que tous les éléments passés dans sont des fichiers. Toutefois, si l’IDE définit l' `SCC_PL_DIR` indicateur dans le `fOptions` paramètre, tous les éléments passés dans sont considérés comme des répertoires. Le plug-in doit ajouter tous les fichiers qui appartiennent aux répertoires. L’IDE ne passera jamais un mélange de fichiers et de répertoires.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [Code de commande](../extensibility/command-code-enumerator.md)
