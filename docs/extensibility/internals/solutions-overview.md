---
title: Présentation des solutions
description: En savoir plus sur les éléments internes d’une solution, pour les développeurs d’extensions qui souhaitent travailler avec des solutions dans les extensions Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91903954f490e5845e01ddbf4b7aa4767f2ceacc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846541"
---
# <a name="solutions-overview"></a>Présentation des solutions

Une solution est un regroupement d’un ou de plusieurs projets qui fonctionnent ensemble pour créer une application. Le projet et les informations d’État relatifs à la solution sont stockés dans deux fichiers solution différents. Le [fichier solution (. sln)](solution-dot-sln-file.md) est basé sur du texte et peut être placé sous le contrôle de code source et partagé entre les utilisateurs. Le [fichier de l’option d’utilisateur de solution (. suo)](solution-user-options-dot-suo-file.md) est binaire. Par conséquent, le fichier. suo ne peut pas être placé sous le contrôle de code source et contient des informations spécifiques à l’utilisateur.

N’importe quel VSPackage peut écrire dans l’un ou l’autre type de fichier solution. En raison de la nature des fichiers, il existe deux interfaces différentes implémentées pour y écrire. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface écrit des informations de texte dans le fichier. sln et l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface écrit des flux binaires dans le fichier. suo.

> [!NOTE]
> Un projet n’a pas besoin d’écrire explicitement une entrée pour elle-même dans le fichier solution ; l’environnement gère cela pour le projet. Par conséquent, à moins que vous ne souhaitiez ajouter du contenu supplémentaire spécifiquement au fichier solution, vous n’avez pas besoin d’inscrire votre VSPackage de cette façon.

Chaque package VSPackage prenant en charge la persistance de solution utilise trois interfaces, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface, qui est implémentée par l’environnement et appelée par le VSPackage, et `IVsPersistSolutionProps` et `IVsPersistSolutionOpts` , qui sont tous deux implémentés par le VSPackage. L' `IVsPersistSolutionOpts` interface doit être implémentée uniquement si des informations privées doivent être écrites par le VSPackage dans le fichier. suo.

Quand une solution est ouverte, le processus suivant a lieu.

1. L’environnement lit la solution.

2. Si l’environnement trouve un `CLSID` , il charge le VSPackage correspondant.

3. Si un VSPackage est chargé, l’environnement appelle `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> l’interface pour l’interface dont le VSPackage a besoin.

   - Lors de la lecture à partir d’un fichier. sln, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionProps` .

   - Lors de la lecture à partir d’un fichier. suo, l’environnement appelle `QueryInterface` pour `IVsPersistSolutionOpts` .

   Vous trouverez des informations spécifiques relatives à l’utilisation de ces fichiers dans la [solution (. Sln)](../../extensibility/internals/solution-dot-sln-file.md) les options utilisateur du fichier et de la [solution (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Si vous souhaitez créer une nouvelle configuration de solution composée de deux configurations de projets et en excluant un tiers de la génération, vous devez utiliser l’interface utilisateur des pages de propriétés ou Automation. Vous ne pouvez pas modifier directement les configurations du gestionnaire de build de solution et leurs propriétés, mais vous pouvez manipuler le gestionnaire de génération de solution à l’aide de la `SolutionBuild` classe de DTE dans le modèle Automation. Pour plus d’informations sur la configuration des solutions, consultez Configuration de la [solution](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
