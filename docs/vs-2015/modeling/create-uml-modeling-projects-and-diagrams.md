---
title: Créer des projets et des diagrammes de modélisation UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52c55b2cfdf000d91a83071b53e8e9450187b720
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852018"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Créer des projets et des diagrammes de modélisation UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles UML vous aident à comprendre, à expliquer et à concevoir les systèmes logiciels. Visual Studio fournit des modèles pour cinq des diagrammes UML les plus fréquemment utilisés : activités, classes, composant, séquence et cas d'usage. En outre, vous pouvez créer des diagrammes de couche, qui vous aideront à définir la structure de votre système.

 Les diagrammes de modélisation UML et les diagrammes de couche ne peuvent exister qu'à l'intérieur d'un projet de modélisation. Chaque projet de modélisation contient un modèle UML partagé et plusieurs diagrammes UML. Chaque diagramme est une vue partielle du modèle. Le modèle UML contient tous les éléments des diagrammes UML et peut être affiché à l'aide de l'Explorateur de modèles UML. Pour plus d’informations sur les modèles et leur relation aux diagrammes, consultez [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md). Pour plus d’informations sur la modélisation des projets sous contrôle de version, consultez [gérer les modèles et les diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md) et [structurer votre solution de modélisation](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Il existe un autre type de diagramme, le diagramme de classes .NET, qui permet de visualiser le code du programme. Pour plus d’informations, consultez [conception et affichage des classes et des types](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="create-a-diagram-in-a-modeling-project"></a><a name="CreatingModelingDiagrams"></a> Créer un diagramme dans un projet de modélisation
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Pour créer un diagramme et l'ajouter à un projet

1. Dans le menu **architecture** , choisissez **nouveau diagramme UML ou diagramme de couche**.

2. Dans la boîte de dialogue **Ajouter un nouveau diagramme** , cliquez sur le type de diagramme de modélisation souhaité.

    ![Boîte de dialogue Ajouter un nouveau diagramme](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Tapez le nom du nouveau diagramme.

4. Dans la zone **Ajouter au projet de modélisation** :

   - Sélectionnez un projet de modélisation qui existe déjà dans votre solution, puis cliquez sur **OK**.

     \- ou -

   1. Sélectionnez **créer un nouveau projet de modélisation**, puis cliquez sur **OK**.

   2. Dans la boîte de dialogue **créer un nouveau projet de modélisation** , tapez un nom et un emplacement pour le nouveau projet, puis cliquez sur **OK**.

        ![Boîte de dialogue Créer un nouveau projet de modélisation](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Si votre solution est ouverte, le nouveau projet est ajouté à la solution. Si vous n'avez aucune solution ouverte, vous pouvez entrer un nom pour une nouvelle solution.

   Si vous disposez déjà d'un projet de modélisation, vous pouvez aussi utiliser la procédure suivante.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Pour ajouter un diagramme à un projet de modélisation existant

1. Dans **Explorateur de solutions**, cliquez sur le nœud du projet de modélisation.

    > [!NOTE]
    > Le projet de modélisation contient un dossier de définition de modèle nommé **ModelDefinition**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** *\<project name>* , sous **modèles**, cliquez sur le type de diagramme de modélisation, par exemple **diagramme de composant UML**.

4. Tapez un nom pour le diagramme, puis cliquez sur **Ajouter**.

     Le diagramme de modélisation s'ouvre et s'affiche dans le projet de modélisation.

    > [!CAUTION]
    > N'ajoutez pas de fichiers de diagramme existants à d'autres projets de modélisation ou à d'autres emplacements de la solution. Il n'est pas possible non plus de les y copier ou de les y faire glisser. De telles actions entraînent la disparition des éléments des diagrammes copiés ou la présence d'erreurs lors de l'ouverture des diagrammes. Vous devez ouvrir le fichier de diagramme à partir du projet de modélisation dans lequel il a été créé. La raison en est qu'un diagramme UML est une vue du modèle appartenant à son projet de modélisation. Pour copier un fichier de diagramme, créez un diagramme et copiez les éléments du diagramme source vers le nouveau diagramme. Pour plus d’informations, consultez [Dépannage des projets et des diagrammes de modélisation](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Pour créer un projet de modélisation vide

1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **nouveau projet** , sous **modèles installés**, cliquez sur **projets de modélisation**.

3. Dans la fenêtre du milieu, cliquez sur **projet de modélisation**.

4. Nommez le projet et spécifiez un emplacement dans les zones **nom** et **emplacement** .

5. Dans la zone **solution** , sélectionnez **Ajouter à la solution** pour ajouter le nouveau projet à une solution que vous avez déjà ouverte. ou **créez une nouvelle solution** pour fermer toute solution ouverte et ajouter le projet à une nouvelle solution.

## <a name="removing-modeling-diagrams-from-a-project"></a><a name="RemovingModelingDiagrams"></a> Suppression de diagrammes de modélisation d’un projet
 Vous pouvez supprimer définitivement un diagramme ou exclure temporairement un diagramme d'un projet, puis le restaurer.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Pour supprimer définitivement un diagramme d'un projet

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier principal qui représente le diagramme, puis cliquez sur **supprimer**.

     Le diagramme est supprimé du projet et du système de fichiers. Les éléments affichés sur le diagramme ne sont pas supprimés de l' **Explorateur de modèles UML**.

    > [!NOTE]
    > Chaque diagramme possède deux fichiers, dont un fichier auxiliaire. Par exemple, si vous avez un diagramme de composant intitulé `CD1`, vous devez supprimer le fichier nommé `CD1.componentdiagram`. Son fichier auxiliaire nommé `CD1.componentdiagram.layout` sera automatiquement supprimé.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Pour exclure temporairement un diagramme d'un projet

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de diagramme, puis cliquez sur **exclure du projet**.

     Le diagramme est supprimé du projet. Il n'est pas supprimé du système de fichiers.

    > [!NOTE]
    > Les éléments affichés sur le diagramme ne sont pas supprimés de l' **Explorateur de modèles UML**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Pour restaurer dans un projet un diagramme exclu temporairement

1. Dans **Explorateur de solutions**, cliquez sur le nœud du projet de modélisation.

    > [!NOTE]
    > Le projet de modélisation contient un dossier de définition de modèle nommé **ModelDefinition**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant** , recherchez le fichier de diagramme, sélectionnez le fichier, puis cliquez sur **Ajouter**.

     Le diagramme de modélisation s'ouvre et s'affiche dans le projet de modélisation.

    > [!NOTE]
    > Chaque diagramme a une paire de fichiers dans le système de fichiers. Ne sélectionnez pas un fichier ayant l’extension `.layout`. En outre, Visual Studio ne prend pas en charge l'ajout de diagrammes UML existants à plusieurs projets de modélisation. Chaque fichier de diagramme doit être ouvert au sein du projet de modélisation dans lequel il a été créé. La raison en est qu'un diagramme UML est une vue du modèle appartenant à son projet de modélisation.

## <a name="diagrams-that-do-not-require-modeling-projects"></a><a name="NonModelDiagrams"></a> Diagrammes qui ne nécessitent pas de projets de modélisation
 Les types de diagrammes suivants ne font pas partie d'un projet de modélisation :

- Diagrammes de classes créés en tant que vues du code source. Ils ne sont pas liés aux diagrammes de classes UML. Pour plus d’informations, consultez [conception et affichage des classes et des types](../ide/designing-and-viewing-classes-and-types.md).

- Cartes de code. Consultez [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Diagrammes qui ne sont pas des diagrammes UML ou des diagrammes de couche, tels que les langages spécifiques du domaine.

## <a name="troubleshooting-modeling-projects-and-diagrams"></a><a name="TroubleshootingModelingProjects"></a> Résolution des problèmes des projets et des diagrammes de modélisation
 Le tableau suivant décrit les problèmes qui peuvent se produire avec les projets de modélisation ou les diagrammes, et explique comment les résoudre :

|**Problème**|**Causes**|**Résolution :**|
|---------------|----------------|--------------------|
|Le projet de modélisation ne peut pas être ouvert ou chargé dans la solution.<br /><br /> Le message suivant s’affiche :<br /><br /> « Un ou plusieurs projets de la solution n'ont pas été correctement chargés. Pour plus d'informations, consultez la fenêtre de Sortie. »<br /><br /> La fenêtre Sortie affiche le message suivant :<br /><br /> «*Nomfichieretcheminduprojetdemodélisation*. modelproj : erreur : format GUID non reconnu. »|Un projet de modélisation possède des références aux projets qui ont le même nom et qui sont dans la même solution.<br /><br /> Par exemple, une couche est liée aux projets qui ont le même nom et qui sont dans la même solution.|Utilisez un éditeur de texte pour ouvrir le fichier du projet de modélisation, supprimez les références et réessayez d'ouvrir le projet de modélisation.<br /><br /> Pour éviter ce problème, n'ajoutez pas de références aux projets qui ont le même nom. Assurez-vous que les projets ont des noms uniques.|
|Il manque des éléments dans les diagrammes qui sont ajoutés, copiés ou déplacés vers d'autres projets de modélisation ou d'autres emplacements de la solution.<br /><br /> - ou -<br /><br /> Les messages suivants s'affichent lorsque vous essayez d'ouvrir un diagramme :<br /><br /> -«Certaines formes ou connecteurs du diagramme sont manquants, car leurs définitions n’existent pas dans ce projet. Les définitions ont été supprimées du modèle pendant que le diagramme était fermé, ou le diagramme a été copié dans un projet ne contenant pas ces définitions. »<br /><br /> - ou -<br /><br /> -« Ce document est ouvert par un autre projet ».|Le fichier de diagramme a été ajouté, déplacé ou copié à partir d'un projet de modélisation vers un autre projet de modélisation ou vers un autre emplacement de la solution.|Pour copier un fichier de diagramme, créez un diagramme et copiez les éléments du diagramme source vers le nouveau diagramme.|

## <a name="see-also"></a>Voir aussi
 [Modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md) [structurer votre solution de modélisation](../modeling/structure-your-modeling-solution.md)
