---
title: API MSBuild | Microsoft Docs
description: En savoir plus sur la surface d’API publique fournie par MSBuild pour permettre à votre programme d’effectuer des builds et d’inspecter des projets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b376f1cb1d6b473c0ea37bb33f6ae2b60789fa24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919310"
---
# <a name="use-the-msbuild-api"></a>Utiliser l’API MSBuild

MSBuild fournit une surface d’API publique qui permet à votre programme d’effectuer des builds et d’inspecter des projets. Les versions récentes des API MSBuild se trouvent dans les packages NuGet suivants :

| Nom du package | Description |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Contient l’assembly Microsoft. Build utilisé pour créer, modifier et évaluer des projets MSBuild.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Contient l’assembly d’infrastructure MSBuild commun utilisé par d’autres assemblys MSBuild. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Fournit une copie exécutable complète de MSBuild. Référencez ce package uniquement si votre application a besoin de charger des projets ou d’exécuter des builds in-process sans nécessiter l’installation de MSBuild. L’évaluation réussie des projets à l’aide de ce package nécessite l’agrégation de composants supplémentaires (comme les compilateurs) dans un répertoire d’application. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Contient l’assembly Microsoft. Build. Tasks qui implémente les tâches couramment utilisées de MSBuild. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Contient l’assembly Microsoft. Build. Utilities utilisé pour implémenter des tâches MSBuild personnalisées. |

En outre, NuGet héberge également un assembly hérité, [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), qui est déconseillé.

Il existe plusieurs versions différentes de l’API MSBuild, et pour les versions 15 et 16, il existe deux formes distinctes des assemblys dans les packages NuGet, l’une compilée avec l' .NET Framework et l’autre avec .NET Core, qui est un sous-ensemble de la surface de l’API .NET Framework.  La version .NET Core de MSBuild est utilisée lorsque vous appelez la `dotnet` commande, et lorsque vous utilisez MSBuild sur des systèmes Mac et Linux.

Vous pouvez trouver la documentation de l’API MSBuild en utilisant le navigateur de l' [API .net](/dotnet/api)ou en parcourant les espaces de noms de la liste suivante.

::: moniker range="vs-2017"
| Espace de noms | S'applique à | Description |
|-----------| -----------| ----------- |
| [Microsoft. Build. construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Tous |  Contient les types que le modèle objet MSBuild utilise pour construire des racines du projet avec des valeurs non-évaluées. Chaque racine du projet correspond à un fichier de projet ou de cibles. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Tous | Contient la `ProjectOptions` classe, qui prend en charge la construction de projet. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Tous | Contient les types que le modèle objet MSBuild utilise pour évaluer des projets. Chaque projet est associé à une ou plusieurs racines de projet. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Tous | Contient la `EvaluationContext` classe utilisée pour stocker l’état d’évaluation entre les appels. |
| [Microsoft. Build. exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Tous | Contient les types d'exceptions susceptibles d'être levés pendant le processus de génération. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Tous | Contient les types que le modèle objet MSBuild utilise pour générer des projets. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Tous | Contient les types qui définissent comment les tâches et les enregistreurs d’événements interagissent avec le moteur MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Tous | Contient les types qui prennent en charge le profilage des performances. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées pour représenter des types XAML analysés à partir de fichiers, de règles et d’autres sources. |
| [Microsoft. Build. globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Tous | Contient des classes qui prennent en charge le traitement de caractères génériques. |
| [Microsoft. Build. globbing. extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Tous | Contient des types qui prennent en charge des extensions pour le traitement de caractères génériques. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Tous | Contient des types qui prennent en charge le `-graph` commutateur MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Tous | Contient les types utilisés pour l'enregistrement de la progression d'une build. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Tous | Contient des types qui prennent en charge la communication à distance dans MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Tous | Contient l’implémentation de toutes les tâches livrées avec MSBuild. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées en interne par MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées par MSBuild.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Tous | Contient des classes utilisées en interne par MSBuild. |
| [Microsoft. Build. Tasks. Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | .NET Framework uniquement | Contient des classes liées aux tâches de génération XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Tous | Contient des classes d’assistance que vous pouvez utiliser pour créer vos propres enregistreurs et tâches MSBuild.|
:::moniker-end
:::moniker range=">=vs-2019"
| Espace de noms | S'applique à | Description |
|-----------| -----------| ----------- |
| [Microsoft. Build. construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Tous |  Contient les types que le modèle objet MSBuild utilise pour construire des racines du projet avec des valeurs non-évaluées. Chaque racine du projet correspond à un fichier de projet ou de cibles. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Tous | Contient la `ProjectOptions` classe, qui prend en charge la construction de projet. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Tous | Contient les types que le modèle objet MSBuild utilise pour évaluer des projets. Chaque projet est associé à une ou plusieurs racines de projet. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Tous | Contient la `EvaluationContext` classe utilisée pour stocker l’état d’évaluation entre les appels. |
| [Microsoft. Build. exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Tous | Contient les types d'exceptions susceptibles d'être levés pendant le processus de génération. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Tous | Contient les types que le modèle objet MSBuild utilise pour générer des projets. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Tous | Contient les types qui définissent comment les tâches et les enregistreurs d’événements interagissent avec le moteur MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Tous | Contient les types qui prennent en charge le profilage des performances. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées pour représenter des types XAML analysés à partir de fichiers, de règles et d’autres sources. |
| [Microsoft. Build. globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Tous | Contient des classes qui prennent en charge le traitement de caractères génériques. |
| [Microsoft. Build. globbing. extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Tous | Contient des types qui prennent en charge des extensions pour le traitement de caractères génériques. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Tous | Contient des types qui prennent en charge le `-graph` commutateur MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Tous | Contient les types utilisés pour l'enregistrement de la progression d'une build. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Tous | Contient des types qui prennent en charge la communication à distance dans MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Tous | Contient l’implémentation de toutes les tâches livrées avec MSBuild. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées en interne par MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | .NET Framework uniquement | Contient des classes utilisées par MSBuild.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Tous | Contient des classes utilisées en interne par MSBuild. |
| [Microsoft. Build. Tasks. Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | .NET Framework uniquement | Contient des classes liées aux tâches de génération XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Tous | Contient des classes d’assistance que vous pouvez utiliser pour créer vos propres enregistreurs et tâches MSBuild.|
:::moniker-end

Dans le tableau précédent, tout dans la colonne s’applique à, les types de l’espace de noms sont disponibles dans les versions .NET Framework et .NET Core de l’API MSBuild.
