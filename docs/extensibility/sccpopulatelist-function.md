---
title: Fonction SccPopulateList (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700533"
---
# <a name="sccpopulatelist-function"></a>Fonction SccPopulateList
Cette fonction met à jour une liste de fichiers pour une commande de contrôle source particulière et fournit l’état de contrôle des sources sur tous les fichiers donnés.

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
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 nCommand (en)

[dans] La commande de contrôle source qui sera `lpFileNames` appliquée à tous les fichiers du tableau (voir code de [commande](../extensibility/command-code-enumerator.md) pour une liste de commandes possibles).

 nFiles

[dans] Nombre de fichiers `lpFileNames` dans le tableau.

 lpFileNames

[dans] Un tableau de noms de fichiers connus de l’IDE.

 pfnPopulate

[dans] La fonction de rappel IDE pour appeler pour ajouter et supprimer les fichiers (voir [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus de détails).

 pvCallerData

[dans] Valeur qui doit être transmise inchangée à la fonction de rappel.

 lpStatus

[dans, dehors] Un tableau pour le plug-in de contrôle source pour retourner les drapeaux d’état pour chaque fichier.

 fOptions

[dans] Drapeaux de commandement (voir la section « Drapeau De la Liste » des [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour plus de détails).

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction examine la liste des fichiers pour son état actuel. Il utilise `pfnPopulate` la fonction de rappel pour aviser l’appelant quand `nCommand`un fichier ne correspond pas aux critères pour le . Par exemple, si `SCC_COMMAND_CHECKIN` la commande est et un fichier dans la liste n’est pas vérifié, puis le rappel est utilisé pour informer l’appelant. De temps en temps, le plug-in de contrôle source peut trouver d’autres fichiers qui pourraient faire partie de la commande et les ajouter. Cela permet, par exemple, à un utilisateur visual basic de consulter un fichier .bmp qui est utilisé par son projet, mais qui n’apparaît pas dans le fichier du projet Visual Basic. Un utilisateur choisit la commande **Get** dans l’IDE. L’IDE affichera une liste de tous les fichiers qu’il pense `SccPopulateList` que l’utilisateur peut obtenir, mais avant que la liste est affichée, la fonction est appelée pour s’assurer que la liste à afficher est à jour.

## <a name="example"></a>Exemple
 L’IDE établit une liste de fichiers qu’il pense que l’utilisateur peut obtenir. Avant d’afficher cette liste, il appelle la `SccPopulateList` fonction, donnant au plug-in de contrôle source la possibilité d’ajouter et de supprimer des fichiers de la liste. Le plug-in modifie la liste en appelant la fonction de rappel donnée (voir [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus de détails).

 Le plug-in continue `pfnPopulate` d’appeler la fonction, qui ajoute et supprime les `SccPopulateList` fichiers, jusqu’à ce qu’il soit terminé, puis revient de la fonction. L’IDE peut alors afficher sa liste. Le `lpStatus` tableau représente tous les fichiers de la liste originale transmise par l’IDE. Le plug-in remplit l’état de tous ces fichiers en plus de faire usage de la fonction de rappel.

> [!NOTE]
> Un plug-in de contrôle source a toujours la possibilité de simplement revenir immédiatement de cette fonction, laissant la liste telle qu’elle est. Si un plug-in implémente cette fonction, `SCC_CAP_POPULATELIST` il peut l’indiquer en définissant le bitflag de capacité dans le premier appel à la [SccInitialize](../extensibility/sccinitialize-function.md). Par défaut, le plug-in doit toujours supposer que tous les éléments étant passés dans les fichiers. Toutefois, si l’IDE place le `SCC_PL_DIR` drapeau dans le `fOptions` paramètre, tous les éléments qui sont transmis doivent être considérés comme des répertoires. Le plug-in doit ajouter tous les fichiers qui appartiennent aux répertoires. L’IDE ne passera jamais dans un mélange de fichiers et d’annuaires.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [Code de commande](../extensibility/command-code-enumerator.md)
