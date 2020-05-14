---
title: Présentation des solutions
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705296"
---
# <a name="solutions-overview"></a>Présentation des solutions

Une solution est un regroupement d’un ou plusieurs projets qui travaillent ensemble pour créer une application. Les informations de projet et d’état relatives à la solution sont stockées dans deux fichiers de solutions différents. Le [fichier solution (.sln)](solution-dot-sln-file.md) est basé sur le texte et peut être placé sous contrôle de code source et partagé entre les utilisateurs. Le [fichier option utilisateur de solution (.suo)](solution-user-options-dot-suo-file.md) est binaire. Par conséquent, le fichier .suo ne peut pas être placé sous contrôle de code source et contient des informations spécifiques à l’utilisateur.

N’importe quel VSPackage peut écrire à l’un ou l’autre type de fichier de solution. En raison de la nature des fichiers, il existe deux interfaces différentes mises en œuvre pour leur écrire. L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> écrit des informations textuelles <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> sur le fichier .sln et l’interface écrit des flux binaires au fichier .suo.

> [!NOTE]
> Un projet n’a pas à écrire explicitement une entrée pour lui-même dans le fichier de solution; l’environnement s’en occupe pour le projet. Par conséquent, à moins que vous ne vouliez ajouter du contenu supplémentaire spécifiquement au fichier de solution, vous n’avez pas besoin d’enregistrer votre VSPackage de cette façon.

Chaque persistance de solution de support VSPackage utilise trois interfaces, l’interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> qui `IVsPersistSolutionProps` `IVsPersistSolutionOpts`est implémentée par l’environnement et appelée par le VSPackage, et qui sont tous deux implémentés par le VSPackage. L’interface `IVsPersistSolutionOpts` n’a besoin d’être implémentée que si des informations privées doivent être écrites par le VSPackage au fichier .suo.

Lorsqu’une solution est ouverte, le processus suivant a lieu.

1. L’environnement lit la solution.

2. Si l’environnement `CLSID`trouve un , il charge le VSPackage correspondant.

3. Si un VSPackage est chargé, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> l’environnement nécessite l’interface `QueryInterface` pour l’interface dont le VSPackage a besoin.

   - Lors de la lecture d’un `QueryInterface` fichier `IVsPersistSolutionProps`.sln, l’environnement exige .

   - Lors de la lecture d’un `QueryInterface` fichier `IVsPersistSolutionOpts`.suo, l’environnement exige .

   Des informations spécifiques relatives à l’utilisation de ces fichiers peuvent être trouvées dans [Solution (. Sln) Options](../../extensibility/internals/solution-dot-sln-file.md) utilisateur de fichiers et [de solutions (. Suo) Fichier](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Si vous souhaitez créer une nouvelle configuration de solution composée de configurations de deux projets et en excluant un tiers de la construction, vous devez utiliser l’interface utilisateur ou l’automatisation des Pages De propriété. Vous ne pouvez pas modifier directement les configurations de gestionnaire de solution et `SolutionBuild` leurs propriétés, mais vous pouvez manipuler le gestionnaire de la solution en utilisant la classe de DTE dans le modèle d’automatisation. Pour plus d’informations sur les solutions configurantes, voir [Solution Configuration](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
