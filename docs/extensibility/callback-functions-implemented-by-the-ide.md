---
title: Fonctions de rappel mises en œuvre par l’IDE Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739893"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Fonctions de rappel mises en œuvre par l’IDE
Pour rendre l’intégration à l’environnement de développement intégré (IDE) aussi transparente que possible et pour fournir une expérience unifiée d’utilisateur final, le plug-in de contrôle source peut utiliser des fonctions de rappel qui sont implémentées par l’IDE. Le plug-in peut appeler ces fonctions à des moments appropriés au cours d’une opération de contrôle source pour transmettre des informations à l’IDE; l’IDE peut alors afficher ces informations en tant qu’éléments intégrés dans son interface utilisateur indigène. L’utilisateur a une expérience moins fragmentée dans ce scénario que si le plug-in a utilisé sa propre interface utilisateur.

 Le fichier d’en-tête requis est *scc.h*. L’emplacement par défaut est *'Program Files’VSIP 8.0'EnvSDK’common’inc\\*. Il est également dans le dossier VSIP qui a l’échantillon de contrôle source plug-in à *'Program Files 'VSIP 8.0 'MSSCCI\\*.

## <a name="in-this-section"></a>Contenu de cette section
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Décrit la fonction de rappel utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages du plug-in de contrôle source par l’intermédiaire de l’IDE.

- [POPLISTFUNC (EN)](../extensibility/poplistfunc.md) Décrit la fonction de rappel qui est utilisée par [SccPopulateList](../extensibility/sccpopulatelist-function.md) lorsque l’IDE n’a pas un accès complet à des informations qui ne sont disponibles que pour le plug-in de contrôle source, comme une liste complète des fichiers sous contrôle de version.

- [REQUÊTE CHANGEFUNC](../extensibility/querychangesfunc.md) Décrit la fonction de rappel utilisée par l’opération [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Décrit la fonction de rappel qui est utilisée par l’opération [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Décrit la fonction de rappel définie par un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) qui permet au plug-in de contrôle source de communiquer les changements de nom vers l’IDE.

## <a name="related-sections"></a>Sections connexes
- [SccOpenProjet](../extensibility/sccopenproject-function.md) Ouvre un projet.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examine la liste des fichiers pour leur état actuel. En outre, `pfnPopulate` utilise la fonction pour informer l’appelant quand un `nCommand`fichier ne correspond pas aux critères pour le .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Examine une liste d’annuaires et de fichiers dans un projet ou des projets qui sont sous contrôle source. Chaque répertoire et nom de fichier trouvé est transmis à une fonction de rappel.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Examine les modifications de nom qui ont été apportées à une liste de fichiers. Chaque nom de fichier est transmis à une fonction de rappel ainsi que son statut de changement.

- [SccSetOption](../extensibility/sccsetoption-function.md) Définit une grande variété d’options. Chaque option `SCC_OPT_xxx` commence par et a son propre ensemble défini de valeurs.

- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md) Décrit le contenu de la section de référence du SDK rechargeable de contrôle source.
