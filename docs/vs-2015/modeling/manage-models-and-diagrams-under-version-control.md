---
title: Gérer des modèles et des diagrammes sous contrôle de version | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 76e8c92707279979cec6406bd1bcd5ad44a1f315
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825781"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Gérer des modèles et des diagrammes sous la gestion de version
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gérez les différentes versions de vos projets et diagrammes de modélisation, notamment les cartes de code (fichiers .dgml), à l’aide du [contrôle de version Team Foundation ou de Git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314), avec une version locale de Team Foundation Server ou dans le cloud avec Visual Studio Team Services.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
> Faites attention quand plusieurs utilisateurs travaillent sur le même projet de modélisation. Découvrez comment vous pouvez [organiser les modèles dans des projets de taille moyenne ou grande](../modeling/structure-your-modeling-solution.md).  
  
## <a name="ModelingProjects"></a> Fichiers dans un projet de modélisation  
 Plusieurs utilisateurs peuvent travailler sur un projet de modélisation en même temps, à condition qu’ils travaillent sur des fichiers différents.  
  
 Pour éviter ou résoudre les conflits entre les modifications apportées par différents utilisateurs, il est important de comprendre comment le modèle est stocké dans les fichiers.  
  
- Chaque package est stocké dans un fichier **.uml** distinct, qui est conservé dans le dossier du projet **ModelDefinition** . Le modèle comporte également un fichier **.uml** . Si un de ces fichiers est supprimé ou endommagé, le package ou modèle correspondant est perdu.  
  
- Chaque diagramme est stocké dans deux fichiers. Par exemple, un diagramme de classes a :  
  
  - **DiagramName.classdiagram** - Si ce fichier est supprimé ou endommagé, le diagramme est perdu, mais les classes et les associations qu’il comportait restent dans le modèle et peuvent être consultées dans l’Explorateur de modèles UML.  

  - **DiagramName.classdiagram.layout** - Si ce fichier est supprimé, les formes continuent d’apparaître dans le diagramme, mais leurs tailles et leurs positions sont perdues. Chaque fichier de disposition est accessoire par rapport à un fichier de diagramme. Pour l’afficher, cliquez sur le [+] en regard du fichier de diagramme dans l’Explorateur de solutions.  
  
> [!NOTE]
> Il est important de maintenir la cohérence entre les fichiers. Par exemple, si vous utilisez le contrôle de code source pour annuler des modifications apportées à un fichier .uml, annulez les modifications correspondantes dans les fichiers .*diagram et .layout en même temps. Éléments représentés dans un. \*fichier de diagramme seront perdue si elles ne sont pas également représentés dans un fichier .uml.  
  
## <a name="Shared"></a> Travailler sur partagé des projets de modélisation  
 Pour réduire les conflits liés au travail simultané sur différentes parties d’un projet :  
  
- Divisez votre projet de modélisation en plusieurs packages représentant différents domaines de travail. Déplacez l’ensemble du modèle dans les packages, au lieu de le laisser dans le modèle racine. Pour plus d’informations, consultez [définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md).  
  
- Les différents utilisateurs ne doivent pas travailler sur le même package ou diagramme en même temps.  
  
- Si vous utilisez des profils, assurez-vous que tout le monde a installé les mêmes. Consultez [personnaliser votre modèle avec des profils et stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
- Pour vous assurer que vous modifiez uniquement le package sur lequel vous travaillez :  
  
  - Définissez la propriété **LinkedPackage** d’un diagramme de classes, de composant ou de cas d’usage UML.  

  - Dans l’Explorateur de modèles UML, faites glisser une activité ou une interaction dans votre package dès que vous l’avez créée. Cet élément apparaît alors dans l’Explorateur de modèles UML quand vous créez le premier nœud dans le diagramme d’activités ou de séquence.  
  
- Pour vous aider à effectuer le suivi des packages, renommez les fichiers de package pour refléter les noms réels des packages.  
  
- Dans [!INCLUDE[esprscc](../includes/esprscc-md.md)], effectuez toujours les opérations **Archiver** et **Obtenir la dernière version** sur le projet de modélisation complet, jamais sur des fichiers individuels.  
  
- Effectuez toujours une opération **Obtenir** immédiatement avant d’archiver le projet de modélisation.  
  
- Fermez toujours tous les diagrammes avant d’effectuer une opération **Obtenir** .  
  
    > [!NOTE]
    > Si un fichier est ouvert quand vous effectuez une opération **Obtenir**et que l’opération entraîne des modifications locales, vous êtes invité à recharger le fichier. Dans ce cas, cliquez sur **Non**, puis rechargez l’ensemble du projet. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet de modélisation, cliquez sur **Décharger le projet**, puis sur **Recharger le projet**.  
  
### <a name="Exclusive"></a> Modifications qui requièrent un accès exclusif au modèle  
 Avant d’apporter les types suivants de modifications, assurez-vous d’avoir un verrou d’extraction sur l’ensemble du projet.  
  
- Renommer ou supprimer des éléments qui sont référencés à partir d’autres packages.  
  
- Modifier les propriétés de relations qui traversent les limites du package.  
  
- Pour en savoir plus sur les verrous d’extraction, consultez [Extraire et modifier des fichiers](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Pour déplacer un fichier de diagramme dans un dossier de projet ou l’en retirer  
  
1. Démarrez l’ **invite de commandes développeur pour Visual Studio**.  
  
2. Utilisez **tf rename** pour déplacer le fichier de diagramme et son fichier **.layout** :  
  
     `tf rename sourcePath targetPath`  
  
3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier, puis cliquez sur **Exclure du projet**.  
  
4. Ajoutez le fichier au dossier de destination.  
  
     Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier de destination ou le projet, pointez sur **Ajouter**, puis cliquez sur **Élément existant**. Dans la boîte de dialogue, sélectionnez le fichier de diagramme, puis cliquez sur **Ajouter**. Le fichier de disposition est ajouté automatiquement.  
  
    > [!NOTE]
    > Vous ne pouvez pas déplacer le fichier vers un autre projet.  
  
## <a name="Merging"></a> Fusion des modifications dans les fichiers de modèle et de diagrammes  
 Une fois que plusieurs utilisateurs ont travaillé simultanément sur un modèle, [!INCLUDE[esprscc](../includes/esprscc-md.md)] vous invite à fusionner les modifications apportées aux fichiers du modèle. Le fait de travailler sur des projets distincts comme décrit dans les sections précédentes permet d’éviter la plupart des fusions. En règle générale, les conflits restants peuvent être automatiquement fusionnés en toute sécurité. Les types de modifications suivants ne doivent entraîner aucune difficulté :  
  
- Types de lignes de vie. Quand vous ajoutez une ligne de vie à une interaction (diagramme de séquence), son type est stocké dans le modèle racine, sauf si vous avez créé la ligne de vie à partir d’un type existant.  
  
- De nouvelles activités et interactions sont initialement stockées dans le modèle racine.  
  
- Ajout d’éléments et de relations.  
  
- Renommer ou supprimer des éléments qui sont référencés uniquement dans leur propre package.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse et modélisation de l’Architecture](../modeling/analyze-and-model-your-architecture.md)   
 [Partager des modèles et exporter des diagrammes](../modeling/share-models-and-exporting-diagrams.md)
