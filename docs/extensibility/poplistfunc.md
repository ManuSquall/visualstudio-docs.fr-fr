---
title: POPLISTFUNC | Microsoft Docs
description: En savoir plus sur la fonction de rappel POPLISTFUNC, qui est utilisée par le plug-in de contrôle de code source pour mettre à jour une liste de fichiers ou de répertoires.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52ed40397793b44f8a9c7ed9c36aa5996ae0176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900380"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Ce rappel est fourni à l' [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l’IDE et est utilisé par le plug-in de contrôle de code source pour mettre à jour une liste de fichiers ou de répertoires (également fournis à la `SccPopulateList` fonction).

 Quand un utilisateur choisit la commande **obtenir** dans l’IDE, l’IDE affiche une zone de liste de tous les fichiers que l’utilisateur peut obtenir. Malheureusement, l’IDE ne connaît pas la liste exacte de tous les fichiers que l’utilisateur peut obtenir ; seul le plug-in contient cette liste. Si d’autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent apparaître dans la liste, mais l’IDE ne les connaît pas. L’IDE génère une liste des fichiers qu’il estime que l’utilisateur peut obtenir. Avant d’afficher cette liste pour l’utilisateur, elle appelle [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` en donnant au plug-in de contrôle de code source la possibilité d’ajouter et de supprimer des fichiers dans la liste.

## <a name="signature"></a>Signature
 Le plug-in de contrôle de code source modifie la liste en appelant une fonction implémentée par l’IDE avec le prototype suivant :

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData le `pvCallerData` paramètre passé par l’appelant (l’IDE) au [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug-in de contrôle de code source doit supposer rien du contenu de ce paramètre.

 fAddRemove si `TRUE` , `lpFileName` est un fichier qui doit être ajouté à la liste des fichiers. Si `FALSE` , `lpFileName` est un fichier qui doit être supprimé de la liste de fichiers.

 État de nStatus de `lpFileName` (une combinaison des `SCC_STATUS` bits ; pour plus d’informations, consultez le [code d’État du fichier](../extensibility/file-status-code-enumerator.md) ).

 lpFileName chemin d’accès complet du répertoire du nom de fichier à ajouter ou supprimer de la liste.

## <a name="return-value"></a>Valeur retournée

|Valeur|Description|
|-----------|-----------------|
|`TRUE`|Le plug-in peut continuer à appeler cette fonction.|
|`FALSE`|Il y a eu un problème au niveau de l’IDE (par exemple, une situation de mémoire insuffisante). Le plug-in doit arrêter l’opération.|

## <a name="remarks"></a>Remarques
 Pour chaque fichier que le plug-in de contrôle de code source souhaite ajouter ou supprimer dans la liste de fichiers, il appelle cette fonction, en passant le `lpFileName` . L' `fAddRemove` indicateur indique un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre indique l’état du fichier. Lorsque le plug-in SCC a terminé d’ajouter et de supprimer des fichiers, il retourne à partir de l’appel [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

> [!NOTE]
> Le `SCC_CAP_POPULATELIST` bit de capacité est requis pour Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Code d’État du fichier](../extensibility/file-status-code-enumerator.md)
