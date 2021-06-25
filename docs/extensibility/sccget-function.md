---
description: Cette fonction récupère une copie d’un ou plusieurs fichiers pour l’affichage et la compilation, mais pas pour la modification.
title: SccGet fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 805c19b0c326e8389b4e1905edf370ad042aac92
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904550"
---
# <a name="sccget-function"></a>SccGet fonction)
Cette fonction récupère une copie d’un ou plusieurs fichiers pour l’affichage et la compilation, mais pas pour la modification. Dans la plupart des systèmes, les fichiers sont marqués en lecture seule.

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

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms qualifiés complets des fichiers à récupérer.

 fOptions

dans Indicateurs de commande ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite de l’opération d’extraction.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_FILEISCHECKEDOUT|Impossible d’extraire le fichier que l’utilisateur a actuellement extrait.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOSPECIFIEDVERSION|A spécifié une version ou une date/heure non valide.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; le fichier n’a pas été synchronisé.|
|SCC_I_OPERATIONCANCELED|Opération annulée avant la fin.|
|SCC_E_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|

## <a name="remarks"></a>Remarques
 Cette fonction est appelée avec un nombre et un tableau de noms des fichiers à récupérer. Si l’IDE passe l’indicateur `SCC_GET_ALL` , cela signifie que les éléments de `lpFileNames` ne sont pas des fichiers mais des répertoires, et que tous les fichiers sous contrôle de code source dans les répertoires spécifiés doivent être récupérés.

 L' `SCC_GET_ALL` indicateur peut être combiné avec l' `SCC_GET_RECURSIVE` indicateur pour récupérer également tous les fichiers dans les répertoires et les sous-répertoires spécifiés.

> [!NOTE]
> `SCC_GET_RECURSIVE` ne doit jamais être passé sans `SCC_GET_ALL` . Notez également que si les répertoires *C:\a* et *C:\A\B* sont tous deux transmis sur une opération d’extraction récursive, *C:\A\B* et tous ses sous-répertoires seront en fait récupérés deux fois. C’est la responsabilité de l’IDE, et non le plug-in de contrôle de code source, qui permet de s’assurer que les doublons de ce type sont conservés hors du tableau.

 Enfin, même si un plug-in de contrôle de code source spécifiait l' `SCC_CAP_GET_NOUI` indicateur lors de l’initialisation, indiquant qu’il n’a pas d’interface utilisateur pour une commande obtenir, cette fonction peut toujours être appelée par l’IDE pour récupérer des fichiers. L’indicateur signifie simplement que l’IDE n’affiche pas d’élément de menu obtenir et que le plug-in n’est pas censé fournir d’interface utilisateur.

## <a name="rename-files-and-sccget"></a>Renommer des fichiers et SccGet
 Situation : un utilisateur extrait un fichier, par exemple, *a.txt*, et le modifie. Avant de pouvoir archiver *a.txt* , un deuxième utilisateur renomme *a.txt* en *b.txt* dans la base de données de contrôle de code source, extrait *b.txt*, apporte des modifications au fichier et vérifie le fichier dans. Le premier utilisateur souhaite les modifications apportées par le deuxième utilisateur afin que le premier utilisateur renomme sa version locale de *a.txt* fichier en *b.txt* et effectue une récupération sur le fichier. Toutefois, le cache local qui effectue le suivi des numéros de version pense toujours que la première version de *a.txt* est stockée localement et par conséquent, le contrôle de code source ne peut pas résoudre les différences.

 Il existe deux façons de résoudre cette situation où le cache local des versions du contrôle de code source n’est plus synchronisé avec la base de données de contrôle de code source :

1. N’autorisez pas l’attribution d’un nouveau nom à un fichier dans la base de données de contrôle de code source actuellement extrait.

2. Utilisez l’équivalent de « supprimer l’ancien » suivi de « Ajouter nouveau ». L’algorithme suivant est l’un des moyens d’y parvenir.

    1. Appelez la fonction [SccQueryChanges](../extensibility/sccquerychanges-function.md) pour en savoir plus sur le changement de nom de *a.txt* à *b.txt* dans la base de données de contrôle de code source.

    2. Renommez le *a.txt* local en *b.txt*.

    3. Appelez la `SccGet` fonction pour *a.txt* et *b.txt*.

    4. Étant donné que *a.txt* n’existe pas dans la base de données de contrôle de code source, le cache de la version locale est purgé des informations de version de *a.txt* manquantes.

    5. Le fichier *b.txt* extrait est fusionné avec le contenu du fichier de *b.txt* local.

    6. Le fichier *b.txt* mis à jour peut désormais être archivé.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs utilisé par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
