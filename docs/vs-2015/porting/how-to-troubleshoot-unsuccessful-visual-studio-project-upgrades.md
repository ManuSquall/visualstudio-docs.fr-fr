---
title: 'Comment : résoudre les problèmes de mise à niveau d’un projet non réussi | Microsoft Docs'
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
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844448"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Comment : dépanner les échecs de mise à niveau de projets Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parfois, Visual Studio ne peut pas convertir entièrement un projet à partir d’une version antérieure de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si les conseils des sections suivantes ne permettent pas de résoudre votre problème spécifique, vous pouvez trouver plus d’informations sur TechNet [wiki : portail de développement](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Le projet ne s’exécute pas, car les fichiers sont introuvables
 Un fichier projet contient des chemins d’accès aux fichiers codés en dur que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilise pour exécuter le projet quand vous appuyez sur F5. Ces chemins d’accès peuvent inclure l’emplacement de devenv. exe et d’autres fichiers requis. Dans une version mise à niveau de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les chemins d’accès de ces fichiers ont peut-être été modifiés.

#### <a name="to-resolve-incorrect-file-paths"></a>Pour résoudre les chemins d’accès de fichiers incorrects

1. Ouvrez votre fichier projet dans un éditeur de texte.

2. Recherchez les chemins d’accès aux fichiers qui peuvent être incorrects, en particulier ceux qui contiennent un numéro de version [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

3. Modifiez les chemins d’accès aux fichiers incorrects afin qu’ils pointent vers les nouvelles cibles.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Le projet n’est pas généré, car les références ne sont pas valides
 Lorsque vous mettez à niveau [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez également mettre à niveau la version de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Si votre projet contient des références qui ne sont plus disponibles dans la version la plus récente de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ils risquent de ne pas être résolus correctement. Cela est particulièrement probable pour les références qui incluent des numéros de version, par exemple `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Si votre code comporte de nombreuses références non valides, la solution la plus simple consiste à utiliser la fonctionnalité de multi-ciblage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour cibler une version antérieure du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Pour résoudre des références incorrectes

1. Ouvrez votre fichier projet dans un éditeur de texte.

2. Ouvrez les propriétés du projet.

3. Sélectionnez la valeur **Framework cible** correcte. Vous pouvez également modifier la valeur de l’élément `<TargetFrameworkVersion>` directement dans le fichier projet.

   Si vous souhaitez que votre projet s’exécute dans la version mise à niveau [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], vous devez mettre à jour les références pour le projet et également mettre à jour toutes les instructions `Imports` ou `Using` qui appellent les références. Si votre projet est chargé dans l’IDE, vous pouvez mettre à jour les références à l’aide de **Explorateur de solutions** ou de la boîte de dialogue **Gestionnaire de références** .

## <a name="see-also"></a>Voir aussi
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [conversion en ASP.net 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
