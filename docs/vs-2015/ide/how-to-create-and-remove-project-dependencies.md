---
title: 'Procédure : Créer et supprimer des dépendances du projet | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e4ce804664f78bd4ec329f7e4e66008053291c77
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799770"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Procédure : Créer et supprimer les dépendances d’un projet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous générez une solution qui contient plusieurs projets, vous pouvez être amené à générer d’abord certains projets pour générer le code utilisé par les autres projets. Quand un projet utilise un code exécutable généré par un autre projet, le projet qui génère le code une dépendance du projet qui utilise le code. Vous pouvez définir ces relations de dépendance dans la boîte de dialogue **Dépendances du projet**.  
  
### <a name="to-assign-dependencies-to-projects"></a>Pour assigner des dépendances à des projets  
  
1. Dans l'Explorateur de solutions, sélectionnez un projet.  
  
2. Dans le menu **Projet**, choisissez **Dépendances du projet**.  
  
    La boîte de dialogue **Dépendances du projet** s’ouvre.  
  
   > [!NOTE]
   >  L’option **Dépendances du projet** n’est disponible que dans une solution comportant plusieurs projets.  
  
3. Sous l’onglet **Dépendances**, sélectionnez un projet à partir du menu déroulant **Projet**.  
  
4. Dans le champ **Dépend de**, cochez la case de tout autre projet à générer avant ce projet.  
  
   Votre solution doit comporter plusieurs projets pour que vous puissiez créer des dépendances du projet.  
  
### <a name="to-remove-dependencies-from-projects"></a>Pour supprimer des dépendances de projets  
  
1.  Dans l'Explorateur de solutions, sélectionnez un projet.  
  
2.  Dans le menu **Projet**, choisissez **Dépendances du projet**.  
  
     La boîte de dialogue **Dépendances du projet** s’ouvre.  
  
    > [!NOTE]
    >  L’option **Dépendances du projet** n’est disponible que dans une solution comportant plusieurs projets.  
  
3.  Sous l’onglet **Dépendances**, sélectionnez un projet à partir du menu déroulant **Projet**.  
  
4.  Dans le champ **Dépend de**, décochez la case en regard de tout autre projet qui n’est plus une dépendance de ce projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [(NIB) Guide pratique pour Modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
