---
title: ID de composant et de charge de travail de Visual Studio Desktop Express
titleSuffix: ''
description: Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide de la ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 21735c82a318623758f1980a1865a543adde121e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881800"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Répertoire des composants Visual Studio Desktop Express

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail.
* Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express pour Windows Desktop

**ID :** Microsoft.VisualStudio.Workload.WDExpress

**Description :** générez des applications natives et gérées comme WPF, WinForms et Win32 avec modification du code avec prise en charge de la syntaxe, contrôle de code source et gestion des éléments de travail. Inclut la prise en charge de C#, Visual Basic et Visual C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.8.27825.0 | Obligatoire
Microsoft.Component.HelpViewer | Visionneuse de l’aide | 15.6.27323.2 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatoire
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.6.27406.0 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.6.27406.0 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.8.27825.0 | Obligatoire
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 15.9.28107.0 | Obligatoire
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.8.27729.1 | Obligatoire
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.9.28016.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.8.27729.1 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26621.2 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.6.27309.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.8.27825.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilateurs et bibliothèques Visual C++ pour ARM64 | 15.9.28230.55 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | 15.6.27406.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK Windows 10 (10.0.17134.0) | 15.8.27924.0 | Obligatoire

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
n/a | n/a | n/a

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
