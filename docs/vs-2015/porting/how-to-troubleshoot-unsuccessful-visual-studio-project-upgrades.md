---
title: 'Procédure : Résoudre les problèmes de mises à niveau du projet échoue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 1fe975fedb8237762d7dadffceff22203dcb899e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696392"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Procédure : Résoudre les problèmes de mises à niveau du projet Visual Studio échoue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parfois, Visual Studio ne peut pas convertir complètement un projet à partir d’une version antérieure de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si les conseils fournis dans les sections suivantes ne résolvent pas votre problème spécifique, vous pourrez peut-être trouver plus d’informations sur le TechNet [Wiki : Portail de développement](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Le projet ne s’exécute pas, car les fichiers sont introuvables
 Un fichier projet contient des chemins d’accès codés en dur qui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilise pour exécuter le projet lorsque vous appuyez sur F5. Ces chemins d’accès peuvent inclure l’emplacement de devenv.exe et d’autres fichiers requis. Dans une version mise à niveau de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les chemins d’accès de ces fichiers ont été modifiés.

#### <a name="to-resolve-incorrect-file-paths"></a>Pour résoudre les chemins d’accès de fichier incorrect

1. Ouvrez votre fichier projet dans un éditeur de texte.

2. Rechercher les chemins d’accès qui peuvent être incorrects, en particulier ceux qui contiennent un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] numéro de version.

3. Modifier les chemins d’accès de fichier incorrect afin qu’ils pointent vers les nouvelles cibles.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Le projet ne génère pas, car les références ne sont pas valides
 Lorsque vous mettez à niveau [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez également mettre à niveau le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version. Si votre projet contient des références qui sont indisponibles dans le nouveau [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version, ils ne peuvent pas être résolus correctement. Il s’agit surtout pour les références qui incluent des numéros de version, par exemple, `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Si votre code comporte de nombreuses références non valides, la solution la plus simple peut être d’utiliser la fonctionnalité de multi-ciblage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour cibler une version antérieure de le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Pour résoudre des références incorrectes

1. Ouvrez votre fichier projet dans un éditeur de texte.

2. Ouvrez les propriétés du projet.

3. Sélectionnez le bon **Framework cible** valeur. Vous pouvez également modifier la valeur de la `<TargetFrameworkVersion>` élément directement dans le fichier projet.

   Si vous souhaitez que votre projet doit être exécuté dans la mise à niveau [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version, vous devez mettre à jour les références du projet et également mettre à jour les `Imports` ou `Using` instructions qui appellent les références. Si votre projet se charge dans l’IDE, vous pouvez mettre à jour les références à l’aide de **l’Explorateur de solutions** ou **Gestionnaire de références** boîte de dialogue.

## <a name="see-also"></a>Voir aussi
 [/ Mise à niveau de (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [conversion vers ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
