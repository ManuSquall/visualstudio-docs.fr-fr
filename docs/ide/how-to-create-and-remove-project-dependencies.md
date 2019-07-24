---
title: 'Procédure : Créer et supprimer les dépendances d’un projet'
ms.date: 06/21/2017
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
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce26c74aced2dd979f9f9847d5c56ead30f897ce
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415588"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Procédure : Créer et supprimer les dépendances d’un projet

Quand vous générez une solution qui contient plusieurs projets, vous pouvez être amené à générer d’abord certains projets pour générer le code utilisé par les autres projets. Quand un projet utilise un code exécutable généré par un autre projet, le projet qui génère le code une dépendance du projet qui utilise le code. Vous pouvez définir ces relations de dépendance dans la boîte de dialogue **Dépendances du projet**.

## <a name="to-assign-dependencies-to-projects"></a>Pour assigner des dépendances à des projets

1. Dans l’**Explorateur de solutions**, sélectionnez un projet.

2. Dans le menu **Projet**, choisissez **Dépendances du projet**.

    La boîte de dialogue **Dépendances du projet** s’ouvre.

   > [!NOTE]
   > L’option **Dépendances du projet** n’est disponible que dans une solution comportant plusieurs projets.

3. Sous l’onglet **Dépendances**, sélectionnez un projet à partir du menu déroulant **Projet**.

4. Dans le champ **Dépend de**, cochez la case de tout autre projet à générer avant ce projet.

   Votre solution doit comporter plusieurs projets pour que vous puissiez créer des dépendances du projet.

## <a name="to-remove-dependencies-from-projects"></a>Pour supprimer des dépendances de projets

1. Dans l’**Explorateur de solutions**, sélectionnez un projet.

2. Dans le menu **Projet**, choisissez **Dépendances du projet**.

     La boîte de dialogue **Dépendances du projet** s’ouvre.

    > [!NOTE]
    > L’option **Dépendances du projet** n’est disponible que dans une solution comportant plusieurs projets.

3. Sous l’onglet **Dépendances**, sélectionnez un projet à partir du menu déroulant **Projet**.

4. Dans le champ **Dépend de**, décochez la case en regard de tout autre projet qui n’est plus une dépendance de ce projet.

## <a name="see-also"></a>Voir aussi

- [Générer et nettoyer des solutions et des projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Gérer les propriétés des projets et des solutions](managing-project-and-solution-properties.md)
