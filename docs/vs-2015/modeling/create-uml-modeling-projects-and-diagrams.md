---
title: Créer des diagrammes et projets de modélisation UML | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a302feda3e6254667df797cdbef5d199886a4c0c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068325"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Créer des projets et des diagrammes de modélisation UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles UML vous aident à comprendre, à expliquer et à concevoir les systèmes logiciels. Visual Studio fournit des modèles pour cinq des diagrammes UML les plus fréquemment utilisés : activités, classes, composant, séquence et cas d'usage. En outre, vous pouvez créer des diagrammes de couche, qui vous aideront à définir la structure de votre système.  
  
 Les diagrammes de modélisation UML et les diagrammes de couche ne peuvent exister qu'à l'intérieur d'un projet de modélisation. Chaque projet de modélisation contient un modèle UML partagé et plusieurs diagrammes UML. Chaque diagramme est une vue partielle du modèle. Le modèle UML contient tous les éléments des diagrammes UML et peut être affiché à l'aide de l'Explorateur de modèles UML. Pour plus d’informations sur les modèles et leur relation aux diagrammes, consultez [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md). Pour plus d’informations sur les projets de modélisation sous contrôle de version, consultez [gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md) et [structurer votre solution de modélisation](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
>  Il existe un autre type de diagramme, le diagramme de classes .NET, qui permet de visualiser le code du programme. Pour plus d’informations, consultez [conception et affichage des Classes et des Types](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
## <a name="CreatingModelingDiagrams"></a> Créer un diagramme dans un projet de modélisation  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Pour créer un diagramme et l'ajouter à un projet  
  
1. Sur le **Architecture** menu, choisissez **nouveau UML ou diagramme de couche**.  
  
2. Dans le **ajouter un nouveau diagramme** boîte de dialogue, cliquez sur le type de diagramme de modélisation que vous souhaitez.  
  
    ![Boîte de dialogue Nouveau diagramme ajouter](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Tapez le nom du nouveau diagramme.  
  
4. Dans le **ajouter au projet de modélisation** zone :  
  
   - Sélectionnez un projet de modélisation qui existe déjà dans votre solution, puis cliquez sur **OK**.  
  
     \- ou -  
  
   1. Sélectionnez **créer un nouveau projet de modélisation**, puis cliquez sur **OK**.  
  
   2. Dans le **créer un nouveau projet de modélisation** boîte de dialogue, tapez un nom et un emplacement pour le nouveau projet, puis cliquez sur **OK**.  
  
        ![Boîte de dialogue Nouveau projet de modélisation créer](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Si votre solution est ouverte, le nouveau projet est ajouté à la solution. Si vous n'avez aucune solution ouverte, vous pouvez entrer un nom pour une nouvelle solution.  
  
   Si vous disposez déjà d'un projet de modélisation, vous pouvez aussi utiliser la procédure suivante.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Pour ajouter un diagramme à un projet de modélisation existant  
  
1. Dans **l’Explorateur de solutions**, cliquez sur la modélisation nœud du projet.  
  
    > [!NOTE]
    >  Le projet de modélisation contient un dossier de définition de modèle nommé **ModelDefinition**.  
  
2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3. Dans le **ajouter un nouvel élément -**  *\<nom_projet >* boîte de dialogue **modèles**, cliquez sur la modélisation diagramme type, par exemple, **UML Diagramme de composant**.  
  
4. Tapez un nom pour le diagramme, puis cliquez sur **ajouter**.  
  
     Le diagramme de modélisation s'ouvre et s'affiche dans le projet de modélisation.  
  
    > [!CAUTION]
    >  N'ajoutez pas de fichiers de diagramme existants à d'autres projets de modélisation ou à d'autres emplacements de la solution. Il n'est pas possible non plus de les y copier ou de les y faire glisser. De telles actions entraînent la disparition des éléments des diagrammes copiés ou la présence d'erreurs lors de l'ouverture des diagrammes. Vous devez ouvrir le fichier de diagramme à partir du projet de modélisation dans lequel il a été créé. La raison en est qu'un diagramme UML est une vue du modèle appartenant à son projet de modélisation. Pour copier un fichier de diagramme, créez un diagramme et copiez les éléments du diagramme source vers le nouveau diagramme. Pour plus d’informations, consultez [résolution des problèmes des projets de modélisation et des diagrammes](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Pour créer un projet de modélisation vide  
  
1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2. Dans le **nouveau projet** boîte de dialogue **modèles installés**, cliquez sur **projets de modélisation**.  
  
3. Dans la fenêtre du milieu, cliquez sur **projet de modélisation**.  
  
4. Nommez le projet et spécifiez un emplacement dans le **nom** et **emplacement** cases.  
  
5. Dans le **Solution** boîte, sélectionnez **ajouter à la Solution** pour ajouter le nouveau projet à une solution que vous avez déjà ouverte ou **créer une nouvelle Solution** pour fermer les solutions ouvertes et ajouter le projet à une nouvelle solution.  
  
## <a name="RemovingModelingDiagrams"></a> Suppression des diagrammes à partir d’un projet de modélisation  
 Vous pouvez supprimer définitivement un diagramme ou exclure temporairement un diagramme d'un projet, puis le restaurer.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Pour supprimer définitivement un diagramme d'un projet  
  
- Dans **l’Explorateur de solutions**, cliquez sur le fichier principal qui représente le diagramme, puis cliquez sur **supprimer**.  
  
     Le diagramme est supprimé du projet et du système de fichiers. Les éléments indiqués sur le diagramme ne sont pas supprimés à partir de **Explorateur de modèles UML**.  
  
    > [!NOTE]
    >  Chaque diagramme possède deux fichiers, dont un fichier auxiliaire. Par exemple, si vous avez un diagramme de composant intitulé `CD1`, vous devez supprimer le fichier nommé `CD1.componentdiagram`. Son fichier auxiliaire nommé `CD1.componentdiagram.layout` sera automatiquement supprimé.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Pour exclure temporairement un diagramme d'un projet  
  
- Dans **l’Explorateur de solutions**, cliquez sur le fichier de diagramme, puis cliquez sur **exclure du projet**.  
  
     Le diagramme est supprimé du projet. Il n'est pas supprimé du système de fichiers.  
  
    > [!NOTE]
    >  Les éléments indiqués sur le diagramme ne sont pas supprimés à partir de **Explorateur de modèles UML**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Pour restaurer dans un projet un diagramme exclu temporairement  
  
1. Dans **l’Explorateur de solutions**, cliquez sur la modélisation nœud du projet.  
  
    > [!NOTE]
    >  Le projet de modélisation contient un dossier de définition de modèle nommé **ModelDefinition**.  
  
2. Sur le **projet** menu, cliquez sur **ajouter un élément existant**.  
  
3. Dans le **ajouter un élément existant** boîte de dialogue, recherchez le fichier de diagramme, sélectionnez le fichier, puis cliquez sur **ajouter**.  
  
     Le diagramme de modélisation s'ouvre et s'affiche dans le projet de modélisation.  
  
    > [!NOTE]
    >  Chaque diagramme a une paire de fichiers dans le système de fichiers. Ne sélectionnez pas un fichier ayant l’extension `.layout`. En outre, Visual Studio ne prend pas en charge l'ajout de diagrammes UML existants à plusieurs projets de modélisation. Chaque fichier de diagramme doit être ouvert au sein du projet de modélisation dans lequel il a été créé. La raison en est qu'un diagramme UML est une vue du modèle appartenant à son projet de modélisation.  
  
## <a name="NonModelDiagrams"></a> Diagrammes qui ne nécessitent pas de projets de modélisation  
 Les types de diagrammes suivants ne font pas partie d'un projet de modélisation :  
  
- Diagrammes de classes créés en tant que vues du code source. Ils ne sont pas liés aux diagrammes de classes UML. Pour plus d’informations, consultez [conception et affichage des Classes et des Types](../ide/designing-and-viewing-classes-and-types.md).  
  
- Cartes de code. Consultez [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
- Diagrammes qui ne sont pas des diagrammes UML ou des diagrammes de couche, tels que les langages spécifiques du domaine.  
  
## <a name="TroubleshootingModelingProjects"></a> Dépannage des diagrammes et projets de modélisation  
 Le tableau suivant décrit les problèmes qui peuvent se produire avec les projets de modélisation ou les diagrammes, et explique comment les résoudre :  
  
|**Problème**|**Causes**|**Résolution**|  
|---------------|----------------|--------------------|  
|Le projet de modélisation ne peut pas être ouvert ou chargé dans la solution.<br /><br /> Le message suivant s'affiche :<br /><br /> « Un ou plusieurs projets de la solution n'ont pas été correctement chargés. Pour plus d'informations, consultez la fenêtre de Sortie. »<br /><br /> La fenêtre Sortie affiche le message suivant :<br /><br /> «*NomFichierEtCheminDuProjetDeModélisation*.modelproj : erreur : Format de Guid non reconnu. »|Un projet de modélisation possède des références aux projets qui ont le même nom et qui sont dans la même solution.<br /><br /> Par exemple, une couche est liée aux projets qui ont le même nom et qui sont dans la même solution.|Utilisez un éditeur de texte pour ouvrir le fichier du projet de modélisation, supprimez les références et réessayez d'ouvrir le projet de modélisation.<br /><br /> Pour éviter ce problème, n'ajoutez pas de références aux projets qui ont le même nom. Assurez-vous que les projets ont des noms uniques.|  
|Il manque des éléments dans les diagrammes qui sont ajoutés, copiés ou déplacés vers d'autres projets de modélisation ou d'autres emplacements de la solution.<br /><br /> ou<br /><br /> Les messages suivants s'affichent lorsque vous essayez d'ouvrir un diagramme :<br /><br /> -« Des formes ou des connecteurs du diagramme sont manquants, car leurs définitions n’existent pas dans ce projet. Les définitions ont été supprimées du modèle pendant que le diagramme était fermé, ou le diagramme a été copié dans un projet ne contenant pas ces définitions. »<br /><br /> ou<br /><br /> -« Ce document est déjà ouvert par un autre projet ».|Le fichier de diagramme a été ajouté, déplacé ou copié à partir d'un projet de modélisation vers un autre projet de modélisation ou vers un autre emplacement de la solution.|Pour copier un fichier de diagramme, créez un diagramme et copiez les éléments du diagramme source vers le nouveau diagramme.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Structurer votre solution de modélisation](../modeling/structure-your-modeling-solution.md)
