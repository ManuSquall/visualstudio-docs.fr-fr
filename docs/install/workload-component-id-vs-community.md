---
title: "ID de composant et de charge de travail de Visual Studio Community 2017 | Microsoft Docs"
description: "Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide de la ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 04/06/2017
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
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: 4779e32433605932af2a9d89235062b1236f8538
ms.lasthandoff: 04/06/2017

---

# <a name="visual-studio-community-2017-workload-and-component-ids"></a>ID de composant et de charge de travail de Visual Studio Community 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).


## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Éditeur de base de Visual Studio (inclus avec Visual Studio Community 2017)

**ID :** Microsoft.VisualStudio.Workload.CoreEditor

**Description :** Expérience de l’interpréteur de commandes de base de Visual Studio, notamment la modification du code prenant en compte la syntaxe, la gestion de code source et la gestion des éléments de travail.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26208.0 | Obligatoire


## <a name="azure-development"></a>Développement Azure

**ID :** Microsoft.VisualStudio.Workload.Azure

**Description :** SDK Azure, outils et projets pour développer des applications cloud et créer des ressources.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.Component.NetFX.Core.Runtime | Runtime .NET Core | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | 15.0.26208.0 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prérequis pour le développement Azure | 15.0.26323.1 | Obligatoire
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Recommandé
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 15.0.26208.0 | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | SDK Azure Mobile Apps | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Outils de base Azure Resource Manager | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Outils Service Fabric | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils principaux pour Azure Cloud Services | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 15.0.26323.1 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Outils Azure Cloud Services | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Outils Azure Resource Manager | 15.0.26323.1 | Recommandé
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Stockage Azure AzCopy | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.PowerShell.Tools | Outils PowerShell | 3.0.427 | Facultatif
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Facultatif


## <a name="data-storage-and-processing"></a>Traitement et stockage de données

**ID :** Microsoft.VisualStudio.Workload.Data

**Description :** connectez, développez et testez des solutions de données à l’aide de SQL Server, Azure Data Lake, Hadoop ou Azure ML.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | 1.13.22.3147 | Recommandé
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | 7.4.1.767 | Recommandé
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.3.10.1131 | Recommandé
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Recommandé
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 15.0.26208.0 | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Recommandé
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Recommandé
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Recommandé
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Outils de création Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliothèques Azure pour .NET | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Émulateur de calcul Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Émulateur de stockage Azure | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Azure.Waverton | Outils principaux pour Azure Cloud Services | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Recommandé
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 15.0.26323.1 | Recommandé
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 15.0.26208.0 | Facultatif


## <a name="net-desktop-development"></a>Développement .NET Desktop

**ID :** Microsoft.VisualStudio.Workload.ManagedDesktop

**Description :** créez des applications de console, WPF et Windows Forms à l’aide de .NET Framework.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Débogueur juste-à-temps | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26208.0 | Recommandé
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | 15.0.26208.0 | Facultatif
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeClone | Clone de code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendances dynamique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | 15.0.26208.0 | Facultatif


## <a name="game-development-with-unity"></a>Développement de jeux avec Unity

**ID :** Microsoft.VisualStudio.Workload.ManagedGame

**Description :** créez des jeux 2D et 3D avec Unity, un environnement de développement multiplateforme performant.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools pour Unity | 15.0.26323.1 | Obligatoire
Component.UnityEngine | Éditeur Unity | 15.0.26323.1 | Recommandé


## <a name="linux-development-with-c"></a>Développement Linux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Description :** créez et déboguez des applications qui s’exécutent dans un environnement Linux.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.MDD.Linux | Développement en Visual C++ pour Linux | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.0.26208.0 | Obligatoire


## <a name="desktop-development-with-c"></a>Développement Desktop avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeDesktop

**Description :** créez des applications Windows classiques grâce à la puissance de l’ensemble d’outils Visual C++, d’ATL et des fonctionnalités facultatives, telles que MFC et C++/CLI.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Débogueur juste-à-temps | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Outils d’architecture pour C++ | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Fonctionnalités de bureau de base Visual C++ | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ x86 et x64 | 15.0.26403.0 | Recommandé
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Facultatif
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.140 | Ensemble d’outils VC++ 2015.3 v140 (x86, x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et d’ATL (x86 et x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de bibliothèque standard | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.WinXP | Prise en charge de Windows XP pour C++ | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Prise en charge de Windows XP pour C++ | 15.0.26208.0 | Facultatif


## <a name="game-development-with-c"></a>Développement de jeux avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeGame

**Description :** exploitez toute la puissance de C++ pour créer des jeux professionnels reposant sur DirectX, Unreal ou Cocos2D.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Outils de profilage C++ | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ x86 et x64 | 15.0.26403.0 | Recommandé
Component.Cocos | Cocos | 15.0.26323.1 | Facultatif
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Facultatif
Component.Unreal | Programme d’installation Unreal Engine | 15.0.26323.1 | Facultatif
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Facultatif
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.0.26208.0 | Facultatif


## <a name="mobile-development-with-c"></a>Développement mobile avec C++

**ID :** Microsoft.VisualStudio.Workload.NativeMobile

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Obligatoire
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Recommandé
Component.Android.SDK19 | Installation du Android SDK (API de niveau 19 et 21) | 15.0.26208.0 | Recommandé
Component.Android.SDK22 | Installation du Android SDK (API de niveau 22) | 15.0.26208.0 | Recommandé
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Recommandé
Component.MDD.Android | Outils de développement C++ Android | 15.0.26208.0 | Recommandé
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.13 | Facultatif
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bits) | 11.3.14 | Facultatif
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Facultatif
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 bits) | 12.1.9 | Facultatif
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 bits) | 13.1.6 | Facultatif
Component.Android.SDK23 | Installation du Android SDK (API de niveau 23) | 15.0.26208.0 | Facultatif
Component.Google.Android.Emulator.API23.V2 | Émulateur Google Android (API de niveau 23) | 15.0.26208.0 | Facultatif
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | Facultatif
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Facultatif
Component.JavaJDK | Kit de développement Java SE (8.0.1120.15) | 15.0.26403.0 | Facultatif
Component.MDD.IOS | Outils de développement C++ iOS | 15.0.26208.0 | Facultatif


## <a name="net-core-cross-platform-development"></a>Développement multiplateforme .NET Core

**ID :** Microsoft.VisualStudio.Workload.NetCoreTools

**Description :** générez des applications multiplateformes à l’aide de .NET Core, ASP.NET Core, HTML, JavaScript et CSS.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | 15.0.26208.0 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 15.0.26323.1 | Recommandé


## <a name="mobile-development-with-net"></a>Développement mobile en .NET

**ID :** Microsoft.VisualStudio.Workload.NetCrossPlat

**Description :** créez des applications multiplateformes pour iOS, Android ou Windows à l’aide de Xamarin.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Recommandé
Component.Android.SDK23 | Installation du Android SDK (API de niveau 23) | 15.0.26208.0 | Recommandé
Component.Google.Android.Emulator.API23.V2 | Émulateur Google Android (API de niveau 23) | 15.0.26208.0 | Recommandé
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | Recommandé
Component.JavaJDK | Kit de développement Java SE (8.0.1120.15) | 15.0.26403.0 | Recommandé
Component.Xamarin | Xamarin | 15.0.26323.1 | Recommandé
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26228.0 | Recommandé
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.26228.0 | Recommandé
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.0.26228.0 | Recommandé
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Recommandé
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Facultatif
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Facultatif
Microsoft.VisualStudio.Component.CodeClone | Clone de code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendances dynamique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Émulateur Windows 10 Mobile (Creators Update) | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Outils de plateforme Windows universelle pour Xamarin | 15.0.26403.0 | Facultatif


## <a name="aspnet-and-web-development"></a>Développement web et ASP.NET

**ID :** Microsoft.VisualStudio.Workload.NetWeb

**Description :** générez des applications web à l’aide de ASP.NET, ASP.NET Core, HTML, JavaScript et CSS.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Core.Component.SDK | Outils de développement .NET Core 1.0.1 | 15.0.26208.0 | Obligatoire
Microsoft.NetCore.ComponentGroup.Web | Outils de développement .NET Core 1.0 - 1.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Recommandé
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DockerTools | Outils de développement de conteneur | 15.0.26323.1 | Recommandé
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Recommandé
Microsoft.Net.Component.4.6.2.SDK | SDK .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.2.TargetingPack | Pack de ciblage .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.7.SDK | SDK .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.Component.4.7.TargetingPack | Pack de ciblage .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Outils de développement .NET Framework 4.6.2 | 15.0.26208.0 | Facultatif
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Outils de développement .NET Framework 4.7 | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeClone | Clone de code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendances dynamique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.FSharp | Prise en charge du langage F# | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.0.26208.0 | Facultatif


## <a name="nodejs-development"></a>Développement Node.js

**ID :** Microsoft.VisualStudio.Workload.Node

**Description :** créez des applications réseau évolutives à l’aide de Node.js, d’un runtime JavaScript asynchrone piloté par les événements.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Node.Tools | Prise en charge de Node.js | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Recommandé
Microsoft.VisualStudio.Component.Git | Git pour Windows | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Facultatif
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Facultatif


## <a name="officesharepoint-development"></a>Développement Office/SharePoint

**ID :** Microsoft.VisualStudio.Workload.Office

**Description :** créez des compléments Office et SharePoint, des solutions SharePoint et des compléments VSTO à l’aide de C#, VB et JavaScript.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.9.170119.3 | Obligatoire
Microsoft.VisualStudio.Component.Debugger.JustInTime | Débogueur juste-à-temps | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Outils de développement .NET Desktop | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Sharepoint.Tools | Outils de développement Office pour Visual Studio | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Web | Outils de développement web et ASP.NET | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools pour Office (VSTO) | 15.0.26228.0 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Facultatif


## <a name="universal-windows-platform-development"></a>Développement de la plateforme universelle Windows

**ID :** Microsoft.VisualStudio.Workload.Universal

**Description :** créez des applications pour la plateforme Windows universelle en C#, VB, JavaScript ou éventuellement C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obligatoire
Microsoft.ComponentGroup.Blend | Blend pour Visual Studio | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.UWP.Support | Outils de plateforme Windows universelle | 15.0.26403.0 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.0.26403.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Outils de plateforme Windows universelle pour Cordova | 15.0.26403.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Outils de plateforme Windows universelle pour Xamarin | 15.0.26403.0 | Obligatoire
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Recommandé
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeClone | Clone de code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendances dynamique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Graphics.Tools | Débogueur graphique et profileur GPU pour DirectX | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Graphics.Win81 | Outils graphiques Windows 8.1 SDK | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Émulateur Windows 10 Mobile (Creators Update) | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK Windows 10 (10.0.15063.0) pour UWP : C++ | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Outils de plateforme Windows universelle C++ | 15.0.26403.0 | Facultatif


## <a name="visual-studio-extension-development"></a>Développement d’une extension Visual Studio

**ID :** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Description :** créez des modules complémentaires et des extensions pour Visual Studio, y compris de nouvelles commandes, des analyseurs de code et des fenêtres d’outil.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.PortableLibrary | Pack de ciblage de bibliothèque portable .NET | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prérequis pour le développement d’extensions Visual Studio | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CodeClone | Clone de code | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.CodeMap | Carte du code | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validation de dépendances dynamique | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.GraphDocument | Éditeur DGML | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Outils d’analyse et d’architecture | 15.0.26208.0 | Recommandé
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Facultatif
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Facultatif
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Facultatif
Microsoft.VisualStudio.Component.ClassDesigner | Concepteur de classes | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.DslTools | SDK Modeling | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et d’ATL (x86 et x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VSSDK | SDK Visual Studio | 15.0.26208.0 | Facultatif


## <a name="mobile-development-with-javascript"></a>Développement mobile avec JavaScript

**ID :** Microsoft.VisualStudio.Workload.WebCrossPlat

**Description :** créez des applications Android, iOS et UWP à l’aide des outils pour Apache Cordova.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Ensemble d’outils Cordova 6.3.1 | 15.0.26323.1 | Obligatoire
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Cordova | Développement mobile avec fonctionnalités de base JavaScript | 15.0.26323.1 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostics JavaScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Prise en charge du langage JavaScript et TypeScript | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK TypeScript 2.1 | 15.0.26208.0 | Obligatoire
Component.Android.SDK23 | Installation du Android SDK (API de niveau 23) | 15.0.26208.0 | Facultatif
Component.Google.Android.Emulator.API23.V2 | Émulateur Google Android (API de niveau 23) | 15.0.26208.0 | Facultatif
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | Facultatif
Component.JavaJDK | Kit de développement Java SE (8.0.1120.15) | 15.0.26403.0 | Facultatif
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.26208.0 | Facultatif
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Facultatif
Microsoft.VisualStudio.Component.DiagnosticTools | Outils de profilage | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Git | Git pour Windows | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Graphics | Éditeurs d’images et de modèles 3D | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Émulateur Windows 10 Mobile (Creators Update) | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK Windows 10 (10.0.15063.0) pour UWP : C#, VB, JS | 15.0.26403.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Outils de plateforme Windows universelle pour Cordova | 15.0.26403.0 | Facultatif
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
Component.Android.Emulator | Émulateur Visual Studio pour Android | 15.0.26208.0
Component.GitHub.VisualStudio | Extension GitHub pour Visual Studio | 2.1.1.4
Microsoft.Component.Blend.SDK.WPF | Blend pour Visual Studio SDK pour .NET | 15.0.26208.0
Microsoft.Component.HelpViewer | Visionneuse d'aide | 15.0.26208.0
Microsoft.Net.Component.3.5.DeveloperTools | Outils de développement .NET Framework 3.5 | 15.0.26208.0
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validation de dépendances | 15.0.26208.0
Microsoft.VisualStudio.Component.LinqToSql | Outils LINQ to SQL | 15.0.26208.0
Microsoft.VisualStudio.Component.Phone.Emulator | Émulateur Windows 10 Mobile (Édition anniversaire) | 15.0.26208.0
Microsoft.VisualStudio.Component.TestTools.Core | Fonctionnalités de base des outils de test | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK TypeScript 2.0 | 15.0.26208.0

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

