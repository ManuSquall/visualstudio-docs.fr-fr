---
title: ID de composant et de charge de travail de Visual Studio Build Tools 2017
description: ID de composant et de charge de travail Visual Studio pour créer des applications Windows classiques
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
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
ms.openlocfilehash: 958e4e842468e871cd9aa65f0a20b87a84aeb4ca
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607859"
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
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Outils de build Azure Cloud Services | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Outils de développement de conteneur - Build Tools | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK TypeScript 3.1 | 15.0.28218.60 | Obligatoire
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.8.27729.1 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | Outils de développement .NET Core 2.1 | 15.8.27924.0 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.2.SDK | Kit SDK .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Outils de développement .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif

## <a name="data-storage-and-processing-build-tools"></a>Outils de build pour le stockage et le traitement des données

**ID :** Microsoft.VisualStudio.Workload.DataBuildTools

**Description :** générer des projets de base de données SQL Server

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.8.27729.1 | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools - Build Tools | 15.8.27825.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé

## <a name="net-desktop-build-tools"></a>Outils de build pour applications de bureau .NET

**ID :** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Description :** outils permettant de générer des applications WPF, Windows Forms et console en C#, Visual Basic et F#.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.Component.ClickOnce.MSBuild | Outils de build ClickOnce | 15.7.27617.1 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | Outils de développement .NET Core 2.1 | 15.8.27924.0 | Recommandé
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.2.SDK | Kit SDK .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Outils de développement .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Core.Component.SDK.1x | Outils de développement .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilateur F# | 15.8.27825.0 | Facultatif

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
Microsoft.Net.Core.Component.SDK.2.1 | Outils de développement .NET Core 2.1 | 15.8.27924.0 | Obligatoire
Microsoft.NetCore.BuildTools.ComponentGroup | Outils de génération .NET Core | 15.8.27906.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Facultatif
Microsoft.Net.Core.Component.SDK.1x | Outils de développement .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facultatif

## <a name="nodejs-build-tools"></a>Outils de génération Node.js

**ID :** Microsoft.VisualStudio.Workload.NodeBuildTools

**Description :**  tâches et cibles MSBuild pour la génération d'applications réseau scalables via Node.js, un runtime JavaScript piloté par des événements asynchrones.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Prise en charge de Node.js MSBuild | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK TypeScript 3.1 | 15.0.28218.60 | Obligatoire

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
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Outils de build pour le développement Office/SharePoint | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.Workflow.BuildTools | Outils de build Windows Workflow Foundation | 15.8.27906.1 | Obligatoire
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.8.27729.1 | Obligatoire
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Outils de build VSTO (Visual Studio Tools pour Office) | 15.7.27617.1 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Recommandé
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.2.SDK | Kit SDK .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Outils de développement .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
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
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Outils VC++ 2017 version 15.9 v14.16 (dernière version v141) | 15.9.28230.55 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Prérequis pour générer des applications de plateforme Windows universelle | 15.8.27705.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 15.8.27924.0 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK Windows 10 (10.0.15063.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [ARM et ARM64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK Windows 10 (10.0.16299.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK Windows 10 (10.0.16299.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK Windows 10 (10.0.15063.0) | 15.8.27825.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK Windows 10 (10.0.16299.0) | 15.8.27825.0 | Facultatif

## <a name="visual-c-build-tools"></a>Outils de génération Visual C++

**ID :** Microsoft.VisualStudio.Workload.VCTools

**Description :** générez des applications de bureau Windows via l'ensemble d'outils Microsoft C++, ATL ou MFC.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Fonctionnalités de base des outils de génération Visual C++ | 15.8.27729.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour redistribuable Visual C++ 2017 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Outils VC++ 2017 version 15.9 v14.16 (dernière version v141) | 15.9.28230.55 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | 15.8.27906.1 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 15.8.27924.0 | Recommandé
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.6.27309.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.VC.140 | Ensemble d’outils VC++ 2015.3 v14.00 (v140) pour le développement d’applications de bureau | 15.7.27617.1 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | ATL Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.6.27309.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de la bibliothèque Standard (expérimental) | 15.6.27309.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.8.27825.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilateurs et bibliothèques Visual C++ pour ARM64 | 15.9.28230.55 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK Windows 10 (10.0.15063.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [x86 et x64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [ARM et ARM64] | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK Windows 10 (10.0.16299.0) pour UWP : C#, VB, JS | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK Windows 10 (10.0.16299.0) pour UWP : C++ | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.WinXP | Prise en charge de Windows XP pour C++ | 15.8.27924.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Prise en charge de Windows XP pour C++ | 15.8.27705.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK Windows 10 (10.0.15063.0) | 15.8.27825.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK Windows 10 (10.0.16299.0) | 15.8.27825.0 | Facultatif

## <a name="visual-studio-extension-development"></a>Développement d’une extension Visual Studio

**ID :** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**Description :** outils pour la génération de composants additionnels et d'extensions pour Visual Studio, notamment des nouvelles commandes, des analyseurs de code et des fenêtres Outil.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.VSSDKBuildTools | Kit Visual Studio SDK Build Tools Core | 15.8.27924.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Prérequis pour le développement d’extensions Visual Studio | 15.8.27729.1 | Obligatoire
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Facultatif
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.6.27406.0 | Facultatif
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | ATL Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC Visual C++ pour x86 et x64 | 15.7.27625.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Outils VC++ 2017 version 15.9 v14.16 (dernière version v141) | 15.9.28230.55 | Facultatif

## <a name="web-development-build-tools"></a>Outils de génération de développement web

**ID :** Microsoft.VisualStudio.Workload.WebBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications web.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK TypeScript 3.1 | 15.0.28218.60 | Obligatoire
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.8.27729.1 | Obligatoire
Microsoft.Component.ClickOnce.MSBuild | Outils de build ClickOnce | 15.7.27617.1 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | Outils de développement .NET Core 2.1 | 15.8.27924.0 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Outils de développement de conteneur - Build Tools | 15.7.27617.1 | Recommandé
Microsoft.VisualStudio.Component.TestTools.BuildTools | Fonctionnalités de base des outils de test - Outils de build | 15.7.27625.0 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Recommandé
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Outils de génération de développement WCF | 15.6.27309.0 | Recommandé
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.2.SDK | Kit SDK .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 15.6.27406.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Outils de développement .NET Framework 4.7.2 | 15.8.27825.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.6.27406.0 | Facultatif
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 2.0 | 15.6.27406.0 | Facultatif
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
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Component.Android.SDK25 | Installation du kit Android SDK (niveau d'API 25) | 15.9.28107.0 | Facultatif
Component.OpenJDK | Distribution Microsoft d’OpenJDK | 15.9.28125.51 | Facultatif

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Name | Version
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK TypeScript 2.0 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK TypeScript 2.2 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | Kit SDK TypeScript 2.3 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | SDK TypeScript 2.5 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | SDK TypeScript 2.6 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | SDK TypeScript 2.7 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | SDK TypeScript 2.8 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | SDK TypeScript 2.9 | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | SDK TypeScript 3.0 | 15.0.27924.0
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
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Bibliothèques VC++ 2017 version 15.9 v14.16 pour Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Bibliothèques VC++ 2017 version 15.9 v14.16 pour Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Bibliothèques VC++ 2017 version 15.9 v14.16 pour Spectre (x86 et x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Ensemble d’outils VC++ 2017 version 15.4 v14.11 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Ensemble d’outils VC++ 2017 version 15.5 v14.12 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Ensemble d’outils VC++ 2017 version 15.6 v14.13 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Ensemble d’outils VC++ 2017 version 15.7 v14.14 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Ensemble d’outils VC++ 2017 version 15.8 v14.15 | 15.0.28230.55

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Outils de génération pour Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
