---
title: ID de composant et de charge de travail de Visual Studio Desktop Express 2017 | Microsoft Docs
description: "Utilisez les ID de composant et de charge de travail pour installer Visual Studio à l’aide de la ligne de commande ou pour spécifier comme dépendance dans un manifeste VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/01/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.workload: multiple
ms.openlocfilehash: a628d2af0ccfaf66c936b391a977a0869139c98b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-desktop-express-2017-workload-and-component-ids"></a>ID de composant et de charge de travail de Visual Studio Desktop Express 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express pour Windows Desktop

**ID :** Microsoft.VisualStudio.Workload.WDExpress

**Description :** générez des applications natives et gérées comme WPF, WinForms et Win32 avec modification du code avec prise en charge de la syntaxe, contrôle de code source et gestion des éléments de travail. Inclut la prise en charge de C#, Visual Basic et Visual C++.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publication ClickOnce | 15.0.27019.1 | Obligatoire
Microsoft.Component.HelpViewer | Visionneuse d'aide | 15.0.27005.2 | Obligatoire
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obligatoire
Microsoft.Component.VC.Runtime.OSSupport | Runtime Visual C++ pour UWP | 15.0.27019.1 | Obligatoire
Microsoft.Net.Component.4.5.1.TargetingPack | Pack de ciblage .NET Framework 4.5.1 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.5.2.TargetingPack | Pack de ciblage .NET Framework 4.5.2 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.5.TargetingPack | Pack de ciblage .NET Framework 4.5 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.6.TargetingPack | Pack de ciblage .NET Framework 4.6 | 15.0.26621.2 | Obligatoire
Microsoft.Net.Component.4.TargetingPack | Pack de ciblage .NET Framework 4 | 15.0.26621.2 | Obligatoire
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Outils de développement .NET Framework 4.6.1 | 15.0.27005.2 | Obligatoire
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Outils de développement .NET Framework 4 - 4.6 | 15.0.26606.0 | Obligatoire
Microsoft.VisualStudio.Component.Common.Azure.Tools | Outils de connectivité et de publication | 1.10.50912.1 | Obligatoire
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.0.26606.0 | Obligatoire
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.NuGet | Gestionnaire de package NuGet | 15.0.27128.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.27019.1 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# et Visual Basic | 15.0.27019.1 | Obligatoire
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime SQL ADAL | 15.0.26606.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CLR | Types de données CLR pour SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitaires de ligne de commande SQL Server | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.DataSources | Sources de données pour la prise en charge de SQL Server | 15.0.26621.2 | Obligatoire
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Obligatoire
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obligatoire
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.TextTemplating | Transformation de modèle de texte | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.0.27019.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilateurs et bibliothèques Visual C++ pour ARM | 15.0.27019.1 | Obligatoire
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilateurs et bibliothèques Visual C++ pour ARM64 | 15.0.27019.1 | Obligatoire
Microsoft.VisualStudio.Component.VisualStudioData | Sources de données et références de service | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [x86 et x64] | 15.0.27128.1 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK Windows 10 (10.0.16299.0) pour plateforme desktop C++ [ARM et ARM64] | 15.0.27128.1 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK Windows 10 (10.0.16299.0) pour UWP : C#, VB, JS | 15.0.27128.1 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK Windows 10 (10.0.16299.0) pour UWP : C++ | 15.0.27128.1 | Obligatoire

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Name | Version
--- | --- | ---
N/A | N/A | N/A

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
