---
title:
- "ID de composant et de charge de travail de Visual Studio Community 2017 | Microsoft Docs"
description: "Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide de la ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX"
keywords: 
author:
- TerryGLee
ms.author:
- tglee
manager:
- ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 58494fc3-12de-4761-bd4a-74b54f72bfb3
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 9055f1352cce133d853d73d378933ddf8b7e3d78
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-community-2017-workload-and-component-ids"></a>ID de composant et de charge de travail de Visual Studio Community 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (ID de composant et de charge de travail de Visual Studio 2017).


## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Éditeur de base de Visual Studio (inclus avec Visual Studio Community 2017)

**ID :** Microsoft.VisualStudio.Workload.CoreEditor

**Description :** l’expérience de l’interpréteur de commandes de base de Visual Studio, notamment la modification du code prenant en compte la syntaxe, le contrôle de code source et la gestion de l’élément de travail.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | Obligatoire


## <a name="azure-development"></a>Développement Azure

**ID :** Microsoft.VisualStudio.Workload.Azure

**Description :** Kit de développement logiciel (SDK) Azure, outils et projets pour développer des applications Cloud et créer des ressources.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.Component.NetFX.Core.Runtime | Runtime .NET Core | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | Obligatoire
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | Obligatoire
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Conditions préalables de développement Azure | Obligatoire
Component.WebSocket | WebSocket4Net | Recommandé
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Kit de développement logiciel (SDK) Azure Mobile Apps | Recommandé
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Outils de base Azure Resource Manager | Recommandé
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Outils Service Fabric | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils de base Azure Cloud Services | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Recommandé
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Recommandé
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Recommandé
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | Recommandé
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Recommandé
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Outils Azure Cloud Services | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Outils Azure Resource Manager | Recommandé
Microsoft.Net.Component.4.6.2.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy de stockage Azure | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | Outils PowerShell | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>Traitement et stockage de données

**ID :** Microsoft.VisualStudio.Workload.Data

**Description :** se connecter, développer et tester des solutions de données à l’aide de SQL Server, Azure Data Lake, Hadoop ou Azure ML.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | Recommandé
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | Recommandé
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | Recommandé
Component.WebSocket | WebSocket4Net | Recommandé
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | Recommandé
Microsoft.Component.MSBuild | MSBuild | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Recommandé
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Recommandé
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Recommandé
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils de base Azure Cloud Services | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Recommandé
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Recommandé
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Recommandé
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Recommandé
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Recommandé
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Recommandé
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | Recommandé
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Recommandé
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Recommandé
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | Optional


## <a name="net-desktop-development"></a>Développement .NET Desktop

**ID :** Microsoft.VisualStudio.Workload.ManagedDesktop

**Description :** créez des applications de console, WPF et Windows Forms à l’aide de .NET Framework.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Outil de débogage juste-à-temps | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Obligatoire
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Outils Entity Framework 6 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Recommandé
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Recommandé
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | Optional
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Outils de développement .NET Core 1.0 - 1.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clone de code | Optional
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendance dynamique | Optional
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | Optional


## <a name="game-development-with-unity"></a>Développement de jeux avec Unity

**ID :** Microsoft.VisualStudio.Workload.ManagedGame

**Description :**créez des jeux 2D et 3D avec Unity, un environnement de développement multiplateforme performant.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools pour Unity | Obligatoire
Component.UnityEngine | Éditeur Unity | Recommandé


## <a name="linux-development-with-c"></a>Développement Linux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Description :** créez et déboguez des applications qui s’exécutent dans un environnement Linux.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.MDD.Linux | Développement en Visual C++ pour Linux | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | Obligatoire


## <a name="desktop-development-with-c"></a>Développement Desktop avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeDesktop

**Description :** créez des applications Windows classiques en vous aidant de la puissance de l’ensemble d’outils Visual C++, ATL et des fonctionnalités facultatives, telles que MFC et C + c++ / CLI.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | Obligatoire
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Outil de débogage juste-à-temps | Obligatoire
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Obligatoire
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Outils d’architecture pour C++ | Obligatoire
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Fonctionnalités de bureau de base en Visual C++ | Obligatoire
Microsoft.VisualStudio.Component.Graphics.Tools | Outil de débogage et profileur GPU pour DirectX | Recommandé
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Recommandé
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Recommandé
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | Optional
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Optional
Microsoft.VisualStudio.Component.VC.140 | Ensemble d’outils VC++ 2015.3 v140 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et ATL (x86 et x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de bibliothèque standard | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Kit de développement logiciel (SDK) Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Kit de développement logiciel (SDK) Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1, SDK | Optional
Microsoft.VisualStudio.Component.WinXP | Prise en charge de Windows XP pour C++ | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Kit de développement logiciel (SDK) Windows 8.1 et UCRT | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Prise en charge de Windows XP pour C++ | Optional


## <a name="game-development-with-c"></a>Développement de jeux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeGame

**Description :** exploitez toute la puissance de C++ pour créer des jeux professionnels reposant sur DirectX, Unreal ou Cocos2D.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | Obligatoire
Microsoft.VisualStudio.Component.Graphics.Tools | Outil de débogage et profileur GPU pour DirectX | Recommandé
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Recommandé
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Recommandé
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Programme d’installation de Unreal Engine | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Optional
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Optional
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Kit de développement logiciel (SDK) Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Kit de développement logiciel (SDK) Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1, SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Kit de développement logiciel (SDK) Windows 8.1 et UCRT | Optional


## <a name="mobile-development-with-c"></a>Développement mobile avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeMobile

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Obligatoire
Component.Android.NDK.R13B | Android NDK (R13B) | Recommandé
Component.Android.SDK19 | Programme d’installation du Kit de développement logiciel Android SDK (API niveau 19 et 21) | Recommandé
Component.Android.SDK22 | Programme d’installation du Kit de développement logiciel Android SDK (API niveau 22) | Recommandé
Component.Ant | Apache Ant (1.9.3) | Recommandé
Component.MDD.Android | Outils de développement Android C++ | Recommandé
Component.Android.Emulator | Émulateur Visual Studio pour Android | Optional
Component.Android.NDK.R11C | Android NDK (R11C) | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bits) | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 bits) | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 bits) | Optional
Component.Android.SDK23 | Installation du Kit de développement logiciel (SDK) Android (API de niveau 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Émulateur Android de Google (API de niveau 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Component.MDD.IOS | Outils de développement C++ iOS | Optional


## <a name="net-core-cross-platform-development"></a>Développement multiplateformes .NET Core

**ID :** Microsoft.VisualStudio.Workload.NetCoreTools

**Description :** générez des applications multiplateformes à l’aide de .NET Core, ASP.NET Core, HTML, JavaScript et CSS

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | Recommandé


## <a name="mobile-development-with-net"></a>Développement mobile en .NET

**ID :** Microsoft.VisualStudio.Workload.NetCrossPlat

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de Xamarin.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Component.Android.NDK.R13B | Android NDK (R13B) | Recommandé
Component.Android.SDK23 | Installation du Kit de développement logiciel (SDK) Android (API de niveau 23) | Recommandé
Component.Google.Android.Emulator.API23.V2 | Émulateur Android de Google (API de niveau 23) | Recommandé
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Recommandé
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Recommandé
Component.Xamarin | Xamarin | Recommandé
Component.Xamarin.Inspector | Classeurs Xamarin | Recommandé
Component.Xamarin.Inspector | Xamarin Profiler | Recommandé
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | Recommandé
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.CodeClone | Clone de code | Optional
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendance dynamique | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Optional
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Optional
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Émulateur Windows 10 Mobile (Édition anniversaire) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Outils de plateforme universelle Windows pour Xamarin (2.0) | Optional


## <a name="aspnet-and-web-development"></a>Développement Web et ASP.NET

**ID :** Microsoft.VisualStudio.Workload.NetWeb

**Description :** générez des applications Web à l’aide de ASP.NET, ASP.NET Core, HTML, JavaScript, et CSS.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Recommandé
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Outils Entity Framework 6 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Recommandé
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Recommandé
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Recommandé
Microsoft.Net.Component.4.6.2.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | Optional
Microsoft.VisualStudio.Component.CodeClone | Clone de code | Optional
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendance dynamique | Optional
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Développement Node.js

**ID :** Microsoft.VisualStudio.Workload.Node

**Description :** créez des applications réseau évolutives à l’aide de Node.js, d’un runtime JavaScript asynchrone piloté par les événements.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.Node.Tools | Prise en charge de Node.js | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Recommandé
Microsoft.VisualStudio.Component.Git | Git pour Windows | Recommandé
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Optional


## <a name="officesharepoint-development"></a>Développement Office/SharePoint

**ID :** Microsoft.VisualStudio.Workload.Office

**Description :** créez des compléments Office et SharePoint, des solutions SharePoint et des compléments VSTO à l’aide de C#, VB et JavaScript.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Outil de débogage juste-à-temps | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Sharepoint.Tools | Outils de développement Office pour Visual Studio | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Obligatoire
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatoire
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | Obligatoire
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools pour Office (VSTO) | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Optional


## <a name="universal-windows-platform-development"></a>Développement de la plateforme universelle Windows

**ID :** Microsoft.VisualStudio.Workload.Universal

**Description :** créez des applications pour la plateforme Windows universelle en C#, VB, JavaScript ou éventuellement C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Component.NetFX.Native | .NET Native | Obligatoire
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatoire
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Obligatoire
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Microsoft.VisualStudio.Component.UWP.Support | Outils de plateforme Windows universelle (2.0) | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Outils de plateforme universelle Windows pour Cordova (2.0) | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Outils de plateforme universelle Windows pour Xamarin (2.0) | Obligatoire
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Recommandé
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | Optional
Microsoft.VisualStudio.Component.CodeClone | Clone de code | Optional
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendance dynamique | Optional
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Outil de débogage et profileur GPU pour DirectX | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Émulateur Windows 10 Mobile (Édition anniversaire) | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Kit de développement logiciel (SDK) Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Kit de développement logiciel (SDK) Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Outils de plateforme Windows universelle C++ | Optional


## <a name="visual-studio-extension-development"></a>Développement d’une extension Visual Studio

**ID :** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Description :** créez les modules complémentaires et des extensions pour Visual Studio, y compris de nouvelles commandes, des analyseurs de code et des fenêtres d’outil.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | Obligatoire
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Conditions préalables au développement d’une extension Visual Studio | Obligatoire
Microsoft.VisualStudio.Component.CodeClone | Clone de code | Recommandé
Microsoft.VisualStudio.Component.CodeMap | Carte du code | Recommandé
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendance dynamique | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Recommandé
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Recommandé
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | Recommandé
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | Optional
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | Optional
Microsoft.VisualStudio.Component.DslTools | Kit de développement logiciel de modélisation | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | Optional
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et ATL (x86 et x64) | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VSSDK | Kit de développement logiciel Visual Studio | Optional


## <a name="mobile-development-with-javascript"></a>Développement mobile avec JavaScript

**ID :** Microsoft.VisualStudio.Workload.WebCrossPlat

**Description :** créez des applications Android, iOS et UWP à l’aide des outils pour Apache Cordova.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Component.CordovaToolset.6.3.1 | Ensemble d’outils Cordova 6.3.1 | Obligatoire
Component.WebSocket | WebSocket4Net | Obligatoire
Microsoft.VisualStudio.Component.Cordova | Développement mobile avec fonctionnalités de base JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | Kit de développement logiciel (SDK) TypeScript 2.1 | Obligatoire
Component.Android.SDK23 | Installation du Kit de développement logiciel (SDK) Android (API de niveau 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Émulateur Android de Google (API de niveau 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | Publication ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | Optional
Microsoft.VisualStudio.Component.Git | Git pour Windows | Optional
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Émulateur Windows 10 Mobile (Édition anniversaire) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Outils de plateforme universelle Windows pour Cordova (2.0) | Optional
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom
--- | ---
Component.GitHub.VisualStudio | Extension GitHub pour Visual Studio
Microsoft.Component.Blend.SDK.WPF | Blend pour Visual Studio SDK pour .NET
Microsoft.Component.HelpViewer | Visionneuse d'aide
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validation de dépendances
Microsoft.VisualStudio.Component.LinqToSql | Outils LINQ to SQL
Microsoft.VisualStudio.Component.TestTools.Core | Fonctionnalités de base des outils de test
Microsoft.VisualStudio.Component.TypeScript.2.0 | Kit de développement logiciel (SDK) TypeScript 2.0

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

