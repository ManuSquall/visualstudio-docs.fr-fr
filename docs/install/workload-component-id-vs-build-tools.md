---
title:
- "ID de composant et de charge de travail de Visual Studio Build Tools 2017 | Microsoft Docs"
description: "ID de composant et de charge de travail Visual Studio pour créer des applications Windows classiques"
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
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 230d04f93e8e857fc0dbaf018e56567259ac6c38
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Répertoire de composants Visual Studio Build Tools 2017

Les tables de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant cette page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (ID de composant et de charge de travail de Visual Studio 2017).

## <a name="msbuild-tools"></a>MSBuild Tools

**ID :** Microsoft.VisualStudio.Workload.MSBuildTools

**Description :** fournit les outils nécessaires pour générer des applications MSBuild.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obligatoire
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | Obligatoire
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilateurs Roslyn C# et Visual Basic | Obligatoire


## <a name="visual-c-build-tools"></a>Outils de génération Visual C++

**ID :** Microsoft.VisualStudio.Workload.VCTools

**Description :** créez des applications Windows classiques en vous aidant de la puissance de l’ensemble d’outils Visual C++, ATL et des fonctionnalités facultatives, telles que MFC et C + c++ / CLI.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Fonctionnalités de base des outils de génération Visual C++ | Obligatoire
Microsoft.VisualStudio.Component.Windows10SDK | Runtime C Windows universel | Obligatoire
Microsoft.VisualStudio.Component.VC.CMake.Project | Outils Visual C++ pour CMake | Recommandé
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Kit de développement logiciel (SDK) Windows 10 (10.0.14393.0) | Recommandé
Microsoft.Component.VC.Runtime.UCRTSDK | SDK CRT (runtime C) universel pour Windows | Optional
Microsoft.Net.Component.4.6.1.SDK | Kit de développement logiciel (SDK) .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Pack de ciblage .NET Framework 4.6.1 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Outils d’analyse statique | Optional
Microsoft.VisualStudio.Component.VC.ATL | Prise en charge de Visual C++ ATL | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Prise en charge de MFC et ATL (x86 et x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (expérimental) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Prise en charge de C++/CLI | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Fonctionnalités de base de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Modules de bibliothèque standard | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Ensemble d’outils VC++ 2017 v141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Kit de développement logiciel (SDK) Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Kit de développement logiciel (SDK) Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1, SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Kit de développement logiciel (SDK) Windows 8.1 et UCRT | Optional


## <a name="web-development-build-tools"></a>Outils de génération de développement web

**ID :** Microsoft.VisualStudio.Workload.WebBuildTools

**Description :** tâches et cibles MSBuild pour la création d’applications web.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Outils de génération de développement web | Obligatoire
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom
--- | ---
N/A | N/A


## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

