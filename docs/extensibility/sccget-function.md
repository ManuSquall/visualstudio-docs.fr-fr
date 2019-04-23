---
title: Fonction SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b773fc52da702f2563276b4a8e51b6c3651f596
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044491"
---
# <a name="sccget-function"></a>Fonction SccGet
Cette fonction récupère une copie d’un ou plusieurs fichiers pour l’affichage et la compilation, mais ne pas pour la modification. Dans la plupart des systèmes, les fichiers sont marqués comme étant en lecture seule.

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
 pvContext

[in] La structure de contexte du plug-in de contrôle de code source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 nFiles

[in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

[in] Tableau des noms qualifiés complets de fichiers à récupérer.

 fOptions

[in] Indicateurs de commande (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).

 pvOptions

[in] Options spécifiques au plug-in de contrôle source.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Succès de l’opération get.|
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_FILEISCHECKEDOUT|Impossible d’obtenir le fichier que l’utilisateur a extrait.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOSPECIFIEDVERSION|Version non valide ou date/heure spécifié.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; fichier n’a pas été synchronisé.|
|SCC_I_OPERATIONCANCELED|Opération annulée avant la fin.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|

## <a name="remarks"></a>Notes
 Cette fonction est appelée avec un nombre et un tableau de noms des fichiers à récupérer. Si l’IDE passe l’indicateur `SCC_GET_ALL`, cela signifie que les éléments dans `lpFileNames` ne sont pas des fichiers, mais les répertoires et tous les fichiers sous contrôle de code source dans les répertoires donnés doivent être récupérés.

 Le `SCC_GET_ALL` indicateur peut être combiné avec le `SCC_GET_RECURSIVE` indicateur pour récupérer tous les fichiers dans les répertoires donnés et tous les sous-répertoires.

> [!NOTE]
>  `SCC_GET_RECURSIVE` ne doit jamais être passé sans `SCC_GET_ALL`. En outre, notez que si répertoires *C:\A* et *C:\A\B* sont passés sur une opération get récursive, *C:\A\B* et tous ses sous-répertoires sont récupérées en fait deux fois. Il incombe de l’IDE, et pas la source de contrôle du plug-in, pour vous assurer que les doublons telle que celle-ci sont conservées hors du tableau.

 Enfin, même si un contrôle de source plug-in spécifié le `SCC_CAP_GET_NOUI` indicateur lors de l’initialisation, indiquant alors qu’il n’a pas une interface utilisateur pour une commande Get, cette fonction peut toujours être appelée par l’IDE pour récupérer des fichiers. L’indicateur signifie simplement que l’IDE n’affiche pas d’un élément de menu Get et que le plug-in n’est pas supposé fournir toute interface utilisateur.

## <a name="rename-files-and-sccget"></a>Renommer des fichiers et SccGet
 Situation : un utilisateur extrait un fichier, par exemple, *a.txt*et le modifie. Avant de *a.txt* peut être archivé, un second utilisateur renomme *a.txt* à *b.txt* dans la base de données de contrôle de source extrait *b.txt*, rend certaines modifications au fichier et vérifie le fichier. Le premier utilisateur veut les modifications apportées par le second utilisateur pour le premier utilisateur renomme leur version locale de *a.txt* fichier *b.txt* et effectue une opération get sur le fichier. Toutefois, le cache local qui effectue le suivi des numéros de version croit toujours la première version de *a.txt* sont stockées localement et par conséquent, le contrôle de code source ne peut pas résoudre les différences.

 Il existe deux manières de résoudre cette situation où le cache local des versions de contrôle de code source est désynchronisé avec la base de données de contrôle de code source :

1. N’autorisez pas la modification du nom d’un fichier dans la base de données de contrôle de code source qui est actuellement extrait.

2. Effectuer l’équivalent de « suppression ancien » suivie de « Ajouter ». L’algorithme suivant est une façon d’y parvenir.

    1. Appelez le [SccQueryChanges](../extensibility/sccquerychanges-function.md) (fonction) pour en savoir plus sur le changement de nom de *a.txt* à *b.txt* dans la base de données de contrôle de code source.

    2. Renommer l’ordinateur local *a.txt* à *b.txt*.

    3. Appelez le `SccGet` (fonction) pour les deux *a.txt* et *b.txt*.

    4. Étant donné que *a.txt* n’existe pas dans la base de données du contrôle de code source, le cache de la version locale est purgé de champ manquant *a.txt* informations de version.

    5. Le *b.txt* fichier extrait est fusionné avec le contenu de la variable locale *b.txt* fichier.

    6. La mise à jour *b.txt* fichier peut maintenant être archivé.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
