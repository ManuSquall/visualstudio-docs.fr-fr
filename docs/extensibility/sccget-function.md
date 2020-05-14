---
title: Fonction SccGet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700901"
---
# <a name="sccget-function"></a>Fonction SccGet
Cette fonction récupère une copie d’un ou plusieurs fichiers pour la visualisation et la compilation, mais pas pour l’édition. Dans la plupart des systèmes, les fichiers sont étiquetés comme lus uniquement.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure contextuelle du plug-in de contrôle source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers `lpFileNames` spécifiés dans le tableau.

 lpFileNames

[dans] Array de noms de fichiers entièrement qualifiés à récupérer.

 fOptions

[dans] Drapeaux de`SCC_GET_ALL` `SCC_GET_RECURSIVE`commande ( , ).

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Succès de se faire opérer.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle à la source ne prend pas en charge cette opération.|
|SCC_E_FILEISCHECKEDOUT|Impossible d’obtenir le fichier que l’utilisateur a actuellement vérifié.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOSPECIFIEDVERSION|Spécifié une version invalide ou une date/heure.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique; n’a pas été synchronisé.|
|SCC_I_OPERATIONCANCELED|Opération annulée avant l’achèvement.|
|SCC_E_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|

## <a name="remarks"></a>Notes
 Cette fonction est appelée avec un compte et un tableau de noms des fichiers à récupérer. Si l’IDE `SCC_GET_ALL`passe le drapeau, `lpFileNames` cela signifie que les éléments dans ne sont pas des fichiers, mais des répertoires, et que tous les fichiers sous contrôle source dans les répertoires donnés doivent être récupérés.

 Le `SCC_GET_ALL` drapeau peut être `SCC_GET_RECURSIVE` combiné avec le drapeau pour récupérer tous les fichiers dans les répertoires donnés et tous les sous-directeurs ainsi.

> [!NOTE]
> `SCC_GET_RECURSIVE`ne devrait jamais `SCC_GET_ALL`être passé sans . En outre, notez que si les répertoires *C: A* et *C: 'A’B* sont tous deux transmis sur un get récursif, *C: 'A’B* et tous ses sous-directeurs seront effectivement récupérés deux fois. Il incombe à l’IDE— et non au plug-in de contrôle source — de s’assurer que des doublons comme celui-ci sont tenus à l’écart du tableau.

 Enfin, même si un plug-in `SCC_CAP_GET_NOUI` de contrôle source a spécifié le drapeau sur l’initialisation, indiquant qu’il n’a pas d’interface utilisateur pour une commande Get, cette fonction peut encore être appelée par l’IDE pour récupérer des fichiers. Le drapeau signifie simplement que l’IDE n’affiche pas un élément de menu Get et que le plug-in ne devrait pas fournir d’interface utilisateur.

## <a name="rename-files-and-sccget"></a>Renommer les fichiers et SccGet
 Situation: un utilisateur vérifie un fichier, par exemple, *a.txt*, et le modifie. Avant *qu’a.txt* puisse être enregistré, un deuxième utilisateur renomme *a.txt* à *b.txt* dans la base de données de contrôle source, vérifie *b.txt*, apporte quelques modifications au fichier, et vérifie le fichier. Le premier utilisateur veut les modifications apportées par le deuxième utilisateur de sorte que le premier utilisateur renomme leur version locale du fichier *a.txt* à *b.txt* et fait un get sur le fichier. Cependant, le cache local qui garde une trace des numéros de version pense toujours que la première version de *a.txt* est stockée localement et donc le contrôle source ne peut pas résoudre les différences.

 Il existe deux façons de résoudre cette situation où le cache local de versions de contrôle des sources devient désynchronisé avec la base de données de contrôle source:

1. N’autorisez pas le changement de nom d’un fichier dans la base de données de contrôle source qui est actuellement vérifiée.

2. Faites l’équivalent de "supprimer vieux" suivi de "ajouter de nouveau". L’algorithme suivant est une façon d’y parvenir.

    1. Appelez la fonction [SccQueryChanges](../extensibility/sccquerychanges-function.md) pour en savoir plus sur le changement de nom *de a.txt* à *b.txt* dans la base de données de contrôle source.

    2. Rebaptiser le *local a.txt* à *b.txt*.

    3. Appelez `SccGet` la fonction pour *a.txt* et *b.txt*.

    4. Parce *qu’a.txt* n’existe pas dans la base de données de contrôle source, le cache de version locale est purgé des informations manquantes de version *a.txt.*

    5. Le fichier *b.txt* en cours de vérification est fusionné avec le contenu du fichier *local b.txt.*

    6. Le fichier *b.txt* mis à jour peut maintenant être enregistré.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
