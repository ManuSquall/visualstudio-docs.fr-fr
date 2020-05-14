---
title: POPLISTFUNC - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702061"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Ce rappel est fourni à la [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l’IDE et est utilisé par le plug-in de `SccPopulateList` contrôle source pour mettre à jour une liste de fichiers ou d’annuaires (également fournis à la fonction).

 Lorsqu’un utilisateur choisit la commande **Get** dans l’IDE, l’IDE affiche une boîte de liste de tous les fichiers que l’utilisateur peut obtenir. Malheureusement, l’IDE ne connaît pas la liste exacte de tous les fichiers que l’utilisateur pourrait obtenir; seul le plug-in a cette liste. Si d’autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent apparaître dans la liste, mais l’IDE ne les connaît pas. L’IDE établit une liste des fichiers qu’il pense que l’utilisateur peut obtenir. Avant d’afficher cette liste à l’utilisateur, il appelle la [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` donnant au plug-in de contrôle source une chance d’ajouter et supprimer des fichiers de la liste.

## <a name="signature"></a>Signature
 Le plug-in de contrôle source modifie la liste en appelant une fonction IDE-mise en œuvre avec le prototype suivant :

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData `pvCallerData` Le paramètre transmis par l’appelant (l’IDE) à la [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug-in de contrôle source ne doit rien supposer sur le contenu de ce paramètre.

 fAddRemove `TRUE`If `lpFileName` , est un fichier qui doit être ajouté à la liste de fichiers. Si `FALSE` `lpFileName` , est un fichier qui doit être supprimé de la liste de fichiers.

 nStatus Statut `lpFileName` de (une `SCC_STATUS` combinaison des bits; voir [Code de statut du fichier](../extensibility/file-status-code-enumerator.md) pour plus de détails).

 lpFileName Voie d’annuaire complète du nom de fichier pour ajouter ou supprimer de la liste.

## <a name="return-value"></a>Valeur retournée

|Valeur|Description|
|-----------|-----------------|
|`TRUE`|Le plug-in peut continuer à appeler cette fonction.|
|`FALSE`|Il y a eu un problème du côté de l’IDE (comme une situation hors mémoire). Le plug-in devrait cesser de fonctionner.|

## <a name="remarks"></a>Notes
 Pour chaque fichier que le plug-in de contrôle source veut ajouter ou supprimer de `lpFileName`la liste de fichiers, il appelle cette fonction, en passant dans le . Le `fAddRemove` drapeau indique un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre donne l’état du fichier. Lorsque le plug-in SCC a fini d’ajouter et de supprimer les fichiers, il revient de [l’appel SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Le `SCC_CAP_POPULATELIST` bit de capacité est nécessaire pour Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Code d’état du fichier](../extensibility/file-status-code-enumerator.md)
