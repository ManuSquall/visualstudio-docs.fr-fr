---
title: "ID de composant et de charge de travail de Visual Studio Build Tools 2017 | Microsoft Docs"
description: "ID de composant et de charge de travail Visual Studio pour créer des applications Windows classiques"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 05/10/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c8a3b886d32a2860a3b8acdd1cbb7d2830009dd4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Répertoire de composants Visual Studio Build Tools 2017

Les tableaux de cette page listent les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant cette page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’un tableau des composants disponibles pour cette charge de travail.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>MSBuild Tools

**ID :** Microsoft.VisualStudio.Workload.MSBuildTools

**Description :** fournit les outils nécessaires pour générer des applications MSBuild.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.0.26228.0 | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | 15.0.26208.0 | Obligatoire


## <a name="visual-c-build-tools"></a>Outils de génération Visual C++

**ID :** Microsoft.VisualStudio.Workload.VCTools

**Description :** créez des applications Windows classiques en vous aidant de la puissance de l’ensemble d’outils Visual C++, ATL et des fonctionnalités facultatives, telles que MFC et C + c++ / CLI.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Fonctionnalités de base des outils de génération Visual C++ | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | 15.0.26208.0 | Obligatoire
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | 15.0.26208.0 | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK Windows 10 (10.0.15063.0) pour plateforme desktop C++ x86 et x64 | 15.0.26403.0 | Recommandé
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.SDK | SDK .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et d’ATL (x86 et x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base C++ de Visual Studio | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de bibliothèque standard | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK Windows 10 (10.0.10240.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK Windows 10 (10.0.10586.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK Windows 10 (10.0.14393.0) | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.Component.Windows81SDK | SDK Windows 8.1 | 15.0.26208.0 | Facultatif
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK Windows 8.1 et SDK UCRT | 15.0.26208.0 | Facultatif


## <a name="web-development-build-tools"></a>Outils de génération de développement web

**ID :** Microsoft.VisualStudio.Workload.WebBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications web.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | 15.0.26323.1 | Obligatoire
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
N/A | N/A | N/A


## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

