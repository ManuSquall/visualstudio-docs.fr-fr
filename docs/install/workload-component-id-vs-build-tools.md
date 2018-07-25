---
title: ID de composant et de charge de travail de Visual Studio Build Tools 2017
description: ID de composant et de charge de travail Visual Studio pour créer des applications Windows classiques
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 61c07c92f751a768451414e6bef876cbc22ec962
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281249"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Répertoire de composants Visual Studio Build Tools 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail.
* Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="azure-development-build-tools"></a>Outils de build pour le développement Azure

**ID :** Microsoft.VisualStudio.Workload.AzureBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications Azure.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.7.27520.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 15.0.26621.2 | Obligatoire
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Outils de build Azure Cloud Services | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Outils de développement de conteneur - Build Tools | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.7.27604.0 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.8 | SDK TypeScript 2.8 | 15.0.27617.1 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif

## <a name="net-desktop-build-tools"></a>Outils de build pour applications de bureau .NET

**ID :** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Description :** outils permettant de générer des applications WPF, Windows Forms et console en C#, Visual Basic et F#.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.Component.ClickOnce.MSBuild | Outils de build ClickOnce | 15.7.27617.1 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Recommandé
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Core.Component.SDK.1x | Outils de développement .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilateur F# | 15.7.27604.0 | Facultatif

## <a name="msbuild-tools"></a>MSBuild Tools

**ID :** Microsoft.VisualStudio.Workload.MSBuildTools

**Description :** fournit les outils nécessaires pour générer des applications MSBuild.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire

## <a name="net-core-build-tools"></a>Outils de génération .NET Core

**ID :** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Description :** outils permettant de générer des applications en utilisant .NET Core, ASP.NET Core, HTML/JavaScript et des conteneurs.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Obligatoire
Microsoft.NetCore.BuildTools.ComponentGroup | Outils de génération .NET Core | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.Net.Core.Component.SDK.1x | Outils de développement .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facultatif

## <a name="nodejs-build-tools"></a>Outils de génération Node.js

**ID :** Microsoft.VisualStudio.Workload.NodeBuildTools

**Description :** créez des applications réseau évolutives à l’aide de Node.js, d’un runtime JavaScript asynchrone piloté par les événements.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Prise en charge de Node.js | 15.6.27406.0 | Obligatoire

## <a name="officesharepoint-build-tools"></a>Outils de build Office/SharePoint

**ID :** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Description :** générez des compléments Office et SharePoint, ainsi que des compléments VSTO.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Outils de build ClickOnce | 15.7.27617.1 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.7.27520.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Outils de build pour le développement Office/SharePoint | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.7.27604.0 | Obligatoire
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Outils de build VSTO (Visual Studio Tools pour Office) | 15.7.27617.1 | Recommandé
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif

## <a name="universal-windows-platform-build-tools"></a>Outils de génération d’applications de plateforme Windows universelle

**ID :** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Description :** fournit les outils nécessaires à la génération d’applications de plateforme Windows universelle.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obligatoire
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Outils VC++ 2017 version 15.7 v14.14 (dernière version v141) | 15.7.27625.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Prérequis pour générer des applications de plateforme Windows universelle | 15.7.27703.1 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 15.7.27703.1 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK Windows 10 (10.0.16299.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif

## <a name="visual-c-build-tools"></a>Outils de génération Visual C++

**ID :** Microsoft.VisualStudio.Workload.VCTools

**Description :** générez des applications de bureau Windows via l'ensemble d'outils Microsoft C++, ATL ou MFC.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Fonctionnalités de base des outils de génération Visual C++ | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour redistribuable Visual C++ 2017 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Outils VC++ 2017 version 15.7 v14.14 (dernière version v141) | 15.7.27625.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 15.7.27703.1 | Recommandé
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.6.27309.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.VC.140 | Ensemble d’outils VC++ 2015.3 v14.00 (v140) pour le développement d’applications de bureau | 15.7.27617.1 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | ATL Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.6.27309.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de la bibliothèque Standard (expérimental) | 15.6.27309.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilateurs et bibliothèques Visual C++ pour ARM64 | 15.6.27309.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK Windows 10 (10.0.15063.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK Windows 10 (10.0.16299.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK Windows 10 (10.0.16299.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.WinXP | Prise en charge de Windows XP pour C++ | 15.7.27703.1 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Prise en charge de Windows XP pour C++ | 15.7.27703.1 | Facultatif

## <a name="web-development-build-tools"></a>Outils de génération de développement web

**ID :** Microsoft.VisualStudio.Workload.WebBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications web.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.7.27520.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.7.27604.0 | Obligatoire
Microsoft.Component.ClickOnce.MSBuild | Outils de build ClickOnce | 15.7.27617.1 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Outils de développement de conteneur - Build Tools | 15.7.27617.1 | Recommandé
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.8 | SDK TypeScript 2.8 | 15.0.27617.1 | Recommandé
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Core.Component.SDK.1x | Outils de développement .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facultatif

## <a name="mobile-development-with-net"></a>Développement mobile en .NET

**ID :** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Description :** outils permettant de générer des applications multiplateformes pour iOS, Android et Windows en C# et F#.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Component.JavaJDK | Kit de développement Java SE (8.0.1120.15) | 15.6.27406.0 | Recommandé
Component.Android.SDK25 | Installation du kit Android SDK (niveau d'API 25) | 15.6.27413.0 | Facultatif

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Name | Version
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK TypeScript 2.0 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK TypeScript 2.2 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.3 | Kit SDK TypeScript 2.3 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | SDK TypeScript 2.5 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | SDK TypeScript 2.6 | 15.0.27520.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL pour ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL pour ARM avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL pour ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL pour ARM64 avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC pour x86/x64 avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC pour ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC pour ARM avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC pour ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Prise en charge de Visual C++ MFC pour ARM64 avec atténuations Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Bibliothèques VC++ 2017 version 15.7 v14.14 pour Spectre (ARM) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Bibliothèques VC++ 2017 version 15.7 v14.14 pour Spectre (ARM64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Bibliothèques VC++ 2017 version 15.7 v14.14 pour Spectre (x86 et x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Ensemble d’outils VC++ 2017 version 15.4 v14.11 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Ensemble d’outils VC++ 2017 version 15.5 v14.12 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Ensemble d’outils VC++ 2017 version 15.6 v14.13 | 15.0.27625.0

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Outils de génération pour Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
