---
title: Les fonctions de rappel implémentées par l’IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6ee0a81472ea556aaca478a2ff33db93fe871
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321175"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Fonctions de rappel implémentées par l’IDE
Pour faciliter l’intégration avec l’environnement de développement intégré (IDE) comme transparente que possible et pour fournir une expérience unifiée de l’utilisateur final, le plug-in de contrôle de code source peut utiliser les fonctions de rappel qui sont implémentées par l’IDE. Le plug-in peut appeler ces fonctions aux moments opportuns pendant une opération de contrôle de code source pour passer des informations à l’IDE ; l’IDE peut ensuite afficher ces informations comme éléments incorporés dans son interface utilisateur native. L’utilisateur a une expérience moins fragmentée dans ce scénario que si le plug-in employées sa propre interface utilisateur.

 Le fichier d’en-tête requis est *scc.h*. L’emplacement par défaut est *\Program Files\VSIP 8.0\EnvSDK\common\inc\\* . Il est également dans le dossier VSIP qui contient les exemples de plug-in de contrôle de source à *\Program Files\VSIP 8.0\MSSCCI\\* .

## <a name="in-this-section"></a>Dans cette section
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug-in via l’IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) décrit la fonction de rappel qui est utilisée par [SccPopulateList](../extensibility/sccpopulatelist-function.md) lorsque l’IDE n’a pas d’accès complet aux informations qui est disponibles uniquement pour le plug-in, telles qu’une liste complète de contrôle de code source fichiers sous contrôle de version.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) décrit la fonction de rappel qui est utilisée par le [SccQueryChanges](../extensibility/sccquerychanges-function.md) opération.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) décrit la fonction de rappel qui est utilisée par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) opération.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) décrit la fonction de rappel définie par un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) qui permet le contrôle de code source plug-in pour communiquer les modifications de nom dans l’IDE.

## <a name="related-sections"></a>Rubriques connexes
- [SccOpenProject](../extensibility/sccopenproject-function.md) ouvre un projet.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) examine la liste des fichiers pour leur état actuel. En outre, utilise le `pfnPopulate` fonction permettant de notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) examine une liste de répertoires et fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de répertoire et fichier trouvé est passé à une fonction de rappel.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) examine les modifications de nom qui ont été apportées à une liste de fichiers. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.

- [SccSetOption](../extensibility/sccsetoption-function.md) définit un large éventail d’options. Chaque option commence par `SCC_OPT_xxx` et possède son propre ensemble défini de valeurs.

- [Plug-ins de contrôle de source](../extensibility/source-control-plug-ins.md) décrit le contenu de la section de référence du SDK de plug-in de contrôle Source.