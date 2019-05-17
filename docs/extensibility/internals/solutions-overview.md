---
title: Vue d’ensemble des solutions
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe348d3e6b5c896ff4c76965b918d41dfe00328
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859326"
---
# <a name="solutions-overview"></a>Vue d’ensemble des solutions

Une solution est un regroupement d’un ou plusieurs projets qui fonctionnent ensemble pour créer une application. Les informations de projet et d’état relatives à la solution sont stockés dans deux fichiers de solution différent. Le [fichier solution (.sln)](solution-dot-sln-file.md) est en mode texte et peuvent être placés sous contrôle de code source et partagé entre les utilisateurs. Le [fichier des options (.suo) solution utilisateur](solution-user-options-dot-suo-file.md) est binaire. Par conséquent, le fichier .suo ne peuvent pas être placé sous contrôle de code source et contient des informations spécifiques à l’utilisateur.

Un VSPackage peut écrire dans ces deux types de fichier solution. En raison de la nature des fichiers, il existe deux interfaces différentes implémentées pour y écrire. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface écrit les informations de texte dans le fichier .sln et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface écrit des flux de données binaires dans le fichier .suo.

> [!NOTE]
> Un projet n’a pas écrit de façon explicite une entrée pour lui-même dans le fichier de solution ; l’environnement qui gère le projet. Par conséquent, sauf si vous souhaitez ajouter du contenu supplémentaire spécifiquement pour le fichier de solution, il est inutile inscrire votre VSPackage de cette façon.

Chaque VSPackage prenant en charge la persistance de solution utilise trois interfaces, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface, qui est implémenté par l’environnement et appelée par le VSPackage, et `IVsPersistSolutionProps` et `IVsPersistSolutionOpts`, qui sont tous deux implémentés par le VSPackage. Le `IVsPersistSolutionOpts` interface doit uniquement être implémentée si les informations privées doivent être écrits par le VSPackage dans le fichier .suo.

Lorsqu’une solution est ouverte, le processus suivant a lieu.

1. L’environnement lit la solution.

2. Si l’environnement recherche un `CLSID`, il charge le VSPackage correspondant.

3. Si un VSPackage est chargé, l’environnement appelle `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface pour l’interface qui nécessite le VSPackage.

   - Lors de la lecture à partir d’un fichier .sln, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionProps`.

   - Lors de la lecture à partir d’un fichier .suo, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionOpts`.

   Vous trouverez des informations spécifiques relatives à l’utilisation de ces fichiers dans [Solution (. Fichier de sln)](../../extensibility/internals/solution-dot-sln-file.md) et [Options utilisateur de Solution (. Fichier suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Si vous souhaitez créer une nouvelle configuration de solution comprenant des configurations de deux projets et une troisième à exclure de la build, vous devez utiliser l’interface utilisateur de Pages de propriété ou l’automatisation. Vous ne pouvez pas modifier les configurations de gestionnaire de build de solution et leurs propriétés directement, mais vous pouvez manipuler le Gestionnaire de génération de solution à l’aide de la `SolutionBuild` classe dans le modèle automation DTE. Pour plus d’informations sur la configuration de solutions, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>