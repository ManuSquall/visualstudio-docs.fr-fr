---
title: ID de composant et de charge de travail de Visual Studio Community 2019
titleSuffix: ''
description: Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide de la ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 03537e74968e9c4e2fb9ffa42541575813dbca88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437681"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Éditeur de base de Visual Studio (fourni avec Visual Studio Community 2019)

**ID :** Microsoft.VisualStudio.Workload.CoreEditor

**Description :** Expérience de l’interpréteur de commandes de base de Visual Studio, notamment la modification du code prenant en compte la syntaxe, la gestion de code source et la gestion des éléments de travail.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 16.1.28811.260 | Obligatoire
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Page de démarrage de Visual Studio pour les utilisateurs C++ | 16.0.28315.86 | Facultatif

## <a name="azure-development"></a>Développement Azure

**ID :** Microsoft.VisualStudio.Workload.Azure

**Description:** Azure SDKs, outils et projets pour développer des applications cloud et créer des ressources à l’aide de .NET Core et .NET Framework. Comprend également des outils pour la conteneurisation de votre application, y compris le support Docker.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Obligatoire
Component.Microsoft.VisualStudio.Web.AzureFunctions | Outils Azure WebJobs | 16.0.28714.129 | Obligatoire
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.DevelopmentTools (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.Web (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 16.1.28810.153 | Obligatoire
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 16.4.29313.120 | Obligatoire
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Prise en charge du langage F# pour les projets web | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prérequis pour le développement Azure | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Outils Azure WebJobs | 16.0.28621.142 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Obligatoire
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake et outils d’analyse des flux de données | 16.5.29721.120 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Runtime | 16.5.29905.7 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools pour Kubernetes | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Outils de base Azure Resource Manager | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Outils Service Fabric | 16.4.29313.120 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils principaux pour Azure Cloud Services | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Outils de build Azure Cloud Services | 16.3.29207.166 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Outils Azure Cloud Services | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Outils Azure Resource Manager | 16.0.28528.71 | Recommandé
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.TargetingPack (en) | .NET Framework 4.8 pack de ciblage | 16.4.29313.120 | Facultatif
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Outils de développement .NET Framework 4.6.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.8.DeveloperTools (en anglais) | .NET Cadre 4.8 outils de développement | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Stockage Azure AzCopy | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facultatif

## <a name="data-storage-and-processing"></a>Traitement et stockage de données

**ID :** Microsoft.VisualStudio.Workload.Data

**Description :** connectez, développez et testez des solutions de données avec SQL Server, Azure Data Lake ou Hadoop.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Recommandé
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Recommandé
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake et outils d’analyse des flux de données | 16.5.29721.120 | Recommandé
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Recommandé
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommandé
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Recommandé
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 16.1.28810.153 | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 16.4.29313.120 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils principaux pour Azure Cloud Services | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Outils de build Azure Cloud Services | 16.3.29207.166 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Recommandé
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Recommandé
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Recommandé
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.FSharp.Desktop | Prise en charge du langage F# pour poste de travail | 16.0.28315.86 | Facultatif

## <a name="data-science-and-analytical-applications"></a>Applications de science des données et analytiques

**ID :** Microsoft.VisualStudio.Workload.DataScience

**Description:** Langues et outillage pour la création d’applications de science des données, y compris Python et F.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.PythonTools | Prise en charge du langage Python | 16.5.29515.121 | Recommandé
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Recommandé
Microsoft.Component.PythonTools.Web | Prise en charge de Python web | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.FSharp.Desktop | Prise en charge du langage F# pour poste de travail | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Recommandé
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Outils de développement natifs Python | 16.2.29020.229 | Facultatif
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Facultatif

## <a name="net-desktop-development"></a>Développement .NET Desktop

**ID :** Microsoft.VisualStudio.Workload.ManagedDesktop

**Description:** Construisez des applications WPF, Windows Forms et consoles à l’aide de C, Visual Basic et Fmd avec .NET Core et .NET Framework.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | 16.5.29514.35 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | 16.0.28315.86 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Runtime | 16.5.29905.7 | Recommandé
Microsoft.NetCore.Component.DevelopmentTools (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Recommandé
Microsoft.VisualStudio.Component.Debugger.JustInTime | Débogueur juste-à-temps | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Recommandé
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Facultatif
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Facultatif
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.TargetingPack (en) | .NET Framework 4.8 pack de ciblage | 16.4.29313.120 | Facultatif
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Outils de développement .NET Framework 4.6.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.8.DeveloperTools (en anglais) | .NET Cadre 4.8 outils de développement | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.FSharp.Desktop | Prise en charge du langage F# pour poste de travail | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Facultatif
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Facultatif
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging (en anglais seulement) | Outils d’emballage MSIX | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Facultatif

## <a name="game-development-with-unity"></a>Développement de jeux avec Unity

**ID :** Microsoft.VisualStudio.Workload.ManagedGame

**Description :** créez des jeux 2D et 3D avec Unity, un environnement de développement multiplateforme performant.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools pour Unity | 16.0.28315.86 | Obligatoire
Component.UnityEngine.x64 | Unity 2019.2 Rédacteur en chef 64 bits | 16.5.29515.121 | Recommandé
Component.UnityEngine.x86 | Éditeur Unity 5.6 32 bits | 16.1.28811.260 | Recommandé

## <a name="linux-development-with-c"></a>Développement Linux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Description :** créez et déboguez des applications qui s’exécutent dans un environnement Linux.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.MDD.Linux | Développement C++ pour Linux | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Obligatoire
Component.Linux.CMake | Outils C++ CMake pour Linux | 16.2.29003.222 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Recommandé
Component.MDD.Linux.GCC.arm | Outils de développement incorporé et IoT | 16.5.29515.121 | Facultatif

## <a name="desktop-development-with-c"></a>Développement Desktop en C++

**ID :** Microsoft.VisualStudio.Workload.NativeDesktop

**Description:** Construisez des applications CMD modernes pour Windows à l’aide d’outils de votre choix, y compris MSVC, Clang, CMake ou MSBuild.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour de Redistributable C++ 2019 | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Fonctionnalités de bureau de base C++ | 16.2.29012.281 | Obligatoire
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Microsoft.VisualStudio.Component.Debugger.JustInTime | Débogueur juste-à-temps | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Recommandé
Microsoft.VisualStudio.Component.VC.ASAN | AdresseSanitizer (Expérimental) | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.VC.ATL | CMD ATL pour les derniers outils de construction v142 (x86 & x64) | 16.4.29313.120 | Recommandé
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils C++ CMake pour Windows | 16.3.29103.31 | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adaptateur de test pour Boost.Test | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Adaptateur de test pour Google Test | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | Éditeur JSON | 16.3.29207.166 | Recommandé
Component.Incredibuild | IncrediBuild - Accélération de build | 16.5.29721.120 | Facultatif
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facultatif
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 16.0.28625.61 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Facultatif
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | CMD MFC pour les derniers outils de construction v142 (x86 & x64) | 16.4.29313.120 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Support CMD/CLI pour les outils de construction v142 (14,25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Compilateur Clang pour Windows (9.0.0) | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl pour v142 Build Tools (x64/x86) | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules C++ pour Build Tools v142 (x64/x86 – expérimental) | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 Build Tools (v14.16) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK Windows 10 (10.0.16299.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK Windows 10 (10.0.17763.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Outils Clang pour Windows (9.0.0 - x64/x86) | 16.5.29514.35 | Facultatif

## <a name="game-development-with-c"></a>Développement de jeux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeGame

**Description :** exploitez toute la puissance de C++ pour créer des jeux professionnels reposant sur DirectX, Unreal ou Cocos2D.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour de Redistributable C++ 2019 | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.VC.ASAN | AdresseSanitizer (Expérimental) | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Recommandé
Component.Android.NDK.R16B | Kit Android NDK (R16B) | 16.5.29916.74 | Facultatif
Component.Android.SDK25.Private | Installation du kit Android SDK (niveau d’API 25) (installation locale pour le développement mobile en C++) | 16.0.28625.61 | Facultatif
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Facultatif
Component.Cocos | Cocos | 16.0.28315.86 | Facultatif
Component.Incredibuild | IncrediBuild - Accélération de build | 16.5.29721.120 | Facultatif
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facultatif
Component.MDD.Android | Outils de développement C++ Android | 16.0.28517.75 | Facultatif
Component.OpenJDK | OpenJDK (distribution Microsoft) | 16.1.28811.260 | Facultatif
Component.Unreal | Programme d’installation Unreal Engine | 16.1.28810.153 | Facultatif
Component.Unreal.Android | Prise en charge de l’IDE Android pour Unreal Engine | 16.1.28810.153 | Facultatif
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Facultatif
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Facultatif
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 16.0.28516.191 | Facultatif
Microsoft.VisualStudio.Component.NuGet.BuildTools | Cibles NuGet et tâches de génération | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK Windows 10 (10.0.16299.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK Windows 10 (10.0.17763.0) | 16.0.28517.75 | Facultatif

## <a name="mobile-development-with-c"></a>Développement mobile avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeMobile

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Android.SDK25.Private | Installation du kit Android SDK (niveau d’API 25) (installation locale pour le développement mobile en C++) | 16.0.28625.61 | Obligatoire
Component.OpenJDK | OpenJDK (distribution Microsoft) | 16.1.28811.260 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Obligatoire
Component.Android.NDK.R16B | Kit Android NDK (R16B) | 16.5.29916.74 | Recommandé
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Recommandé
Component.MDD.Android | Outils de développement C++ Android | 16.0.28517.75 | Recommandé
Component.Android.NDK.R16B_3264 | Kit Android NDK (R16B) (32 bits) | 16.5.29916.74 | Facultatif
Component.Google.Android.Emulator.API25.Private | Émulateur Android Google (niveau d’API 25) (installation locale) | 16.1.28810.153 | Facultatif
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (installation locale) | 16.0.28528.71 | Facultatif
Component.Incredibuild | IncrediBuild - Accélération de build | 16.5.29721.120 | Facultatif
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facultatif
Component.MDD.IOS | Outils de développement C++ iOS | 16.0.28517.75 | Facultatif

## <a name="net-core-cross-platform-development"></a>Développement multiplateforme .NET Core

**ID :** Microsoft.VisualStudio.Workload.NetCoreTools

**Description :** générez des applications multiplateformes avec .NET Core, ASP.NET Core, HTML/JavaScript et des conteneurs incluant une prise en charge Docker.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Obligatoire
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.DevelopmentTools (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.Web (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Prise en charge du langage F# pour les projets web | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Obligatoire
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Component.Microsoft.VisualStudio.Web.AzureFunctions | Outils Azure WebJobs | 16.0.28714.129 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Runtime | 16.5.29905.7 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 16.1.28810.153 | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 16.4.29313.120 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Outils Azure WebJobs | 16.0.28621.142 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Outils cloud pour le développement web | 16.2.29003.222 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Prise en charge IIS des délais de développement | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging (en anglais seulement) | Outils d’emballage MSIX | 16.4.29409.204 | Facultatif

## <a name="mobile-development-with-net"></a>Développement mobile en .NET

**ID :** Microsoft.VisualStudio.Workload.NetCrossPlat

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de Xamarin.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribution Microsoft) | 16.1.28811.260 | Obligatoire
Component.Xamarin | Xamarin | 16.5.29721.120 | Obligatoire
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.DevelopmentTools (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.Merq | Outils communs internes Xamarin | 16.2.29012.281 | Obligatoire
Microsoft.VisualStudio.Component.MonoDebugger | Débogueur mono | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Moteur de création de modèles ASP.NET | 16.0.28315.86 | Obligatoire
Component.Android.SDK28 | Installation du kit Android SDK (niveau d’API 28) | 16.2.29003.222 | Recommandé

## <a name="aspnet-and-web-development"></a>Développement web et ASP.NET

**ID :** Microsoft.VisualStudio.Workload.NetWeb

**Description:** Construisez des applications Web à l’aide de ASP.NET Core, ASP.NET, HTML/JavaScript et Containers, y compris le support Docker.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Obligatoire
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.DevelopmentTools (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.Web (en anglais seulement) | .NET Outils de développement de base | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Prise en charge du langage F# pour les projets web | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Obligatoire
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Component.Microsoft.VisualStudio.Web.AzureFunctions | Outils Azure WebJobs | 16.0.28714.129 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommandé
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Runtime | 16.5.29905.7 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.AspNet45 | Fonctionnalités ASP.NET avancées | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 16.1.28810.153 | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 16.4.29313.120 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 16.0.28315.86 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Outils Azure WebJobs | 16.0.28621.142 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Outils cloud pour le développement web | 16.2.29003.222 | Recommandé
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.TargetingPack (en) | .NET Framework 4.8 pack de ciblage | 16.4.29313.120 | Facultatif
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Outils de développement .NET Framework 4.6.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.8.DeveloperTools (en anglais) | .NET Cadre 4.8 outils de développement | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Modèles de projet supplémentaires (versions précédentes) | 16.0.28621.142 | Facultatif
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Prise en charge IIS des délais de développement | 16.0.28315.86 | Facultatif

## <a name="nodejs-development"></a>Développement Node.js

**ID :** Microsoft.VisualStudio.Workload.Node

**Description :** créez des applications réseau évolutives à l’aide de Node.js, d’un runtime JavaScript asynchrone piloté par les événements. 

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.Node.Tools | Outils de développement Node.js | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Obligatoire
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Facultatif

## <a name="officesharepoint-development"></a>Développement Office/SharePoint

**ID :** Microsoft.VisualStudio.Workload.Office

**Description :** créez des compléments Office et SharePoint, des solutions SharePoint et des compléments VSTO à l’aide de C#, VB et JavaScript.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Obligatoire
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 16.0.28517.75 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | 16.5.29514.35 | Obligatoire
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.Sharepoint.Tools | Outils de développement Office pour Visual Studio | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obligatoire
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Obligatoire
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools pour Office (VSTO) | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.1.TargetingPack | Pack de ciblage .NET Framework 4.7.1 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.TargetingPack (en) | .NET Framework 4.8 pack de ciblage | 16.4.29313.120 | Facultatif
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Outils de développement .NET Framework 4.6.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Outils de développement .NET Framework 4.7.1 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 16.3.29207.166 | Facultatif
Microsoft.Net.ComponentGroup.4.8.DeveloperTools (en anglais) | .NET Cadre 4.8 outils de développement | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Facultatif

## <a name="python-development"></a>Développement Python

**ID :** Microsoft.VisualStudio.Workload.Python

**Description :** Modification, débogage, développement interactif et contrôle de code source pour Python.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.PythonTools | Prise en charge du langage Python | 16.5.29515.121 | Obligatoire
Component.CPython3.x64 | Python 3 64 bits (3.7.5) | 3.7.5 | Recommandé
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Recommandé
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Recommandé
Microsoft.Component.PythonTools.Web | Prise en charge de Python web | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 16.4.29409.204 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 16.5.29721.120 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Recommandé
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Développement web et ASP.NET | 16.0.28621.142 | Recommandé
Component.CPython2.x64 | Python 2 64 bits (2.7.16) | 2.7.16 | Facultatif
Component.CPython2.x86 | Python 2 32 bits (2.7.16) | 2.7.16 | Facultatif
Component.CPython3.x86 | Python 3 32 bits (3.7.5) | 3.7.5 | Facultatif
Component.Microsoft.VisualStudio.RazorExtension | Services de langage Razor | 16.0.28714.129 | Facultatif
Component.Microsoft.Web.LibraryManager | Gestionnaire de bibliothèques | 16.0.28315.86 | Facultatif
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Facultatif
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Outils de développement natifs Python | 16.2.29020.229 | Facultatif
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Facultatif
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Facultatif
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Facultatif
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Facultatif
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Facultatif
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 16.1.28810.153 | Facultatif
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 16.4.29313.120 | Facultatif
Microsoft.VisualStudio.Component.Azure.Waverton | Outils principaux pour Azure Cloud Services | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Outils de build Azure Cloud Services | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Facultatif
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Driver | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitaires de ligne de commande SQL Server | 16.0.28707.177 | Facultatif
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 16.0.28315.86 | Facultatif
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 16.4.29409.204 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.ComponentGroup.Web | Prérequis des outils de développement web et ASP.NET | 16.4.29318.151 | Facultatif

## <a name="universal-windows-platform-development"></a>Développement de la plateforme universelle Windows

**ID :** Microsoft.VisualStudio.Workload.Universal

**Description:** Créez des applications pour la plate-forme Windows Universelle avec C, VB ou optionnellement C.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | Obligatoire
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | 16.0.28315.86 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 16.0.28517.75 | Obligatoire
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Runtime | 16.5.29905.7 | Obligatoire
Microsoft.NetCore.Component.SDK (en anglais seulement) | SDK .NET Core | 16.5.29905.7 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | 16.0.28517.75 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.18362 | SDK Windows 10 (10.0.18362.0) | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging (en anglais seulement) | Outils d’emballage MSIX | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native et .NET Standard | 16.3.29102.218 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Outils de plateforme Windows universelle | 16.4.29409.204 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Outils de plateforme Windows universelle pour Xamarin | 16.5.29514.35 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Facultatif
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Facultatif
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Prise en charge de la plateforme Windows universelle en C++ pour Build Tools v142 (ARM64) | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités C++ de base | 16.0.28625.61 | Facultatif
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Mise à jour de Redistributable C++ 2019 | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 OUTILS de construction ARM (v14.25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 CMD ARM64 outils de construction (v14.25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.25) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM Build Tools (v14.16) | 16.2.29003.222 | Facultatif
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 Build Tools (v14.16) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 Build Tools (v14.16) | 16.1.28829.92 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK Windows 10 (10.0.16299.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK Windows 10 (10.0.17763.0) | 16.0.28517.75 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 Aperçu SDK (10.0.19041.0) | 16.5.29721.120 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Connectivité des périphériques USB | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Fonctionnalités de bureau de base C++ | 16.2.29012.281 | Facultatif
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Outils de plateforme Windows universelle C++ (v142) | 16.3.29207.166 | Facultatif
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Outils de plateforme Windows universelle C++ (v141) | 16.1.28810.153 | Facultatif

## <a name="visual-studio-extension-development"></a>Développement d’une extension Visual Studio

**ID :** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Description :** créez des modules complémentaires et des extensions pour Visual Studio, y compris de nouvelles commandes, des analyseurs de code et des fenêtres d’outil.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obligatoire
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.7.2.TargetingPack | Pack de ciblage .NET Framework 4.7.2 | 16.0.28517.75 | Obligatoire
Microsoft.Net.Component.4.8.SDK (en) | .NET Cadre 4.8 SDK | 16.4.29313.120 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.7.2 | 16.3.29207.166 | Obligatoire
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 16.1.28829.92 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 16.0.28714.129 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 16.5.29515.121 | Obligatoire
Microsoft.VisualStudio.Component.VSSDK | Kit de développement logiciel Visual Studio | 16.0.28315.86 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prérequis pour le développement d’extensions Visual Studio | 16.4.29318.151 | Obligatoire
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage .NET | 16.5.29515.121 | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 16.0.28625.61 | Recommandé
Microsoft.Component.CodeAnalysis.SDK | SDK .NET Compiler Platform | 16.2.29003.222 | Facultatif
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Facultatif
Microsoft.VisualStudio.Component.DslTools | SDK Modeling | 16.0.28315.86 | Facultatif

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
Component.GitHub.VisualStudio | Extension GitHub pour Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Publication ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Visionneuse de l’aide | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | SDK .NET Framework 4.7.1 | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | Kit SDK .NET Framework 4.7.2 | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 Runtime (EOL) | 16.5.29813.82
Microsoft.Net.Core.Component.SDK.3.0 | .NET Core 3.0 Runtime (EOL) | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Outils de développement plus .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Outils de développement Web plus .NET Core 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Intégration Office pour Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validation de dépendances | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git pour Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Outils LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM Build Tools (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 Build Tools (v14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM64 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ ATL v14.20 pour Build Tools v142 (x86 et x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ ATL v14.20 pour Build Tools v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ ATL v14.20 pour Build Tools v142 avec atténuations de Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ ATL v14.20 pour Build Tools v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ ATL v14.20 pour Build Tools v142 avec atténuations de Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ ATL v14.20 pour Build Tools v142 avec atténuations de Spectre (x86 et x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Prise en charge de C++/CLI pour Build Tools v142 (14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC pour Build Tools v142 (x86 et x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC pour Build Tools v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC pour Build Tools v142 avec atténuations de Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC pour Build Tools v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC pour Build Tools v142 avec atténuations de Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC pour Build Tools v142 avec atténuations de Spectre (x86 et x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 Build Tools (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ x64/x86 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM Build Tools (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 Build Tools (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM64 (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | C++ ATL v14.21 pour Build Tools v142 (x86 et x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | C++ ATL v14.21 pour Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | C++ ATL v14.21 pour Build Tools v142 avec atténuations de Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ ATL v14.21 pour Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ ATL v14.21 pour Build Tools v142 avec atténuations de Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ ATL v14.21 pour Build Tools v142 avec atténuations de Spectre (x86 et x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Prise en charge de C++/CLI pour Build Tools v142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC pour Build Tools v142 (x86 et x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC pour Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v14.21 MFC pour Build Tools v142 avec atténuations de Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v14.21 MFC pour Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | C++ v14.21 MFC pour Build Tools v142 avec atténuations de Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC pour Build Tools v142 avec atténuations de Spectre (x86 et x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 build tools (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ x64/x86 (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 - VS 2019 C++ ARM Build Tools (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ ARM64 Build Tools (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ ARM64 (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | V14.22 ATL pour v142 outils de construction (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | V14.22 ATL pour les outils de construction v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | V14.22 ATL pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | V14.22 ATL pour les outils de construction v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | V14.22 ATL pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | V14.22 ATL pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29515.121
Support Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Prise en charge de C++/CLI pour Build Tools v142 (14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC | V 14,22 MFC pour les outils de construction v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | V 14,22 MFC pour les outils de construction v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | V 14,22 MFC pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | V 14,22 MFC pour les outils de construction v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | V 14,22 MFC pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | V 14,22 MFC pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 Build Tools (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v142 - VS 2019 C++ x64/x86 (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - VS 2019 OUTILS de construction ARM (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 CMD ARM Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - VS 2019 CMD ARM64 outils de construction (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 - VS 2019 CMD ARM64 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | V14.23 ATL pour v142 outils de construction (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | V14.23 ATL pour les outils de construction v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | V14.23 ATL pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | V14.23 ATL pour les outils de construction v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | V14.23 ATL pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | V14.23 ATL pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29515.121
Support Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Support CMD/CLI pour les outils de construction v142 (14,23) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.23.MFC | V 14,23 MFC pour les outils de construction v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | V 14,23 MFC pour les outils de construction v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | V 14,23 MFC pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | V 14,23 MFC pour les outils de construction v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | V 14,23 MFC pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | V 14,23 MFC pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C x64/x86 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - VS 2019 OUTILS de construction ARM (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 CMD ARM Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 - VS 2019 CMD ARM64 outils de construction (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 - VS 2019 CMD ARM64 Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | V14.24 ATL pour v142 outils de construction (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | V14.24 ATL pour les outils de construction v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | V14.24 ATL pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | V14.24 ATL pour les outils de construction v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | V14.24 ATL pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | V14.24 ATL pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29721.120
Support Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Support CMD/CLI pour les outils de construction v142 (14,24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC | V 14,24 MFC pour les outils de construction v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | V 14,24 MFC pour les outils de construction v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | V 14,24 MFC pour v142 outils de construction avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | V 14,24 MFC pour les outils de construction v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | V 14,24 MFC pour v142 outils de construction avec Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | V 14,24 MFC pour v142 outils de construction avec Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 - VS 2019 C x64/x86 outils de construction (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 - VS 2019 C x64/x86 Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM | CMD ATL pour les derniers outils de construction v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | CMD ATL pour les derniers outils de construction v142 avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | CMD ATL pour les derniers outils de construction v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | CMD ATL pour les derniers outils de construction v142 avec Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | CMD ATL pour les derniers outils de construction v142 avec Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | CMD MFC pour les derniers outils de construction v142 avec Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | CMD MFC pour les derniers outils de construction v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | CMD MFC pour les derniers outils de construction v142 avec Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | CMD MFC pour les derniers outils de construction v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | CMD MFC pour les derniers outils de construction v142 avec Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSM de Redistributable C++ 2019 | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 CMD ARM Spectre-mitigated libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 CMD ARM64 Spectre-mitigated libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C x64/x86 Spectre-mitigated libs (v14.25)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | Bibliothèques avec atténuations de Spectre MSVC v141 - VS 2017 C++ ARM (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v141 - VS 2017 C++ ARM64 (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL pour Build Tools v141 (x86 et x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL pour Build Tools v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL pour Build Tools v141 avec atténuations de Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ ATL pour Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++ ATL pour Build Tools v141 avec atténuations de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++ ATL pour Build Tools v141 avec atténuations de Spectre (x86 et x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Prise en charge de C++/CLI pour Build Tools v141 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC pour Build Tools v141 (x86 et x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC pour Build Tools v141 (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC pour Build Tools v141 avec atténuations de Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC pour Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC pour Build Tools v141 avec atténuations de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC pour Build Tools v141 avec atténuations de Spectre (x86 et x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | Bibliothèques avec atténuations de Spectre MSVC v141 - VS 2017 C++ x64/x86 (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Prise en charge de Windows XP en C++ pour les outils VS 2017 (v141) [déprécié] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
