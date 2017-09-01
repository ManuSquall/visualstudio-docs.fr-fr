---
title: "Créer des solutions et des projets | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---

# <a name="create-solutions-and-projects"></a>Créer des solutions et des projets

Les projets sont les conteneurs logiques pour tout ce qui est nécessaire pour générer votre application. Quand vous créez un projet en choisissant **Fichier**, **Nouveau**, **Projet** dans le menu principal, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée une solution pour le contenir. Vous pouvez ensuite si nécessaire ajouter plusieurs projets nouveaux ou existants à la solution. Vous pouvez créer des projets à partir de fichiers de code existants et vous pouvez créer des projets temporaires (.NET uniquement) qui sont supprimés quand vous en avez terminé avec eux.

> [!NOTE]
>  Les descriptions de cette rubrique sont basées sur l'édition Visual Studio Community. Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites ici, selon vos paramètres ou votre version de Visual Studio. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-project-from-an-installed-project-template"></a>Créer un projet à partir d'un modèle de projet installé  
 Choisissez **Fichier**, **Nouveau**, **Projet** dans le menu principal pour afficher la boîte de dialogue Nouveau projet. Dans le volet gauche sous **Installé**, **Modèles**, choisissez le langage de programmation, ainsi que la plateforme ou la technologie, puis choisissez un modèle parmi les modèles disponibles dans le volet du milieu.  

 Dans la boîte de dialogue **Nouveau projet** , la liste déroulante **Solution** vous permet de créer le projet dans une solution nouvelle ou existante, ou dans une nouvelle instance de Visual Studio.  

## <a name="create-a-project-from-existing-code-files"></a>Créer un projet à partir de fichiers de code existants  
 Si vous avez une collection de fichiers non intégrés, vous pouvez facilement créer un projet qui les contient. Choisissez **Fichier**, **Nouveau**, **Projet à partir de code existant** pour démarrer l’Assistant **Créer un projet à partir de fichiers de code existants**, puis suivez les invites.  

> [!TIP]
>  Cette option est la plus appropriée pour une collection de fichiers relativement simple.  

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Créer un projet temporaire (C# et Visual Basic)
 En travaillant avec des projets temporaires, vous pouvez créer et expérimenter un projet .NET sans spécifier un emplacement sur le disque. Quand vous créez un projet, vous sélectionnez simplement un type et un modèle de projet, et vous spécifiez un nom dans la boîte de dialogue **Nouveau projet** . Pendant que vous travaillez avec le projet temporaire, vous pouvez à tout moment l'enregistrer ou vous pouvez l'abandonner.  

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Créer un projet .NET qui cible une version spécifique du .NET Framework  
 Vous pouvez créer un projet pour cibler des versions antérieures du .NET Framework en utilisant le menu déroulant de la version du **.Net Framework** en haut de la boîte de dialogue **Nouveau projet** . Définissez cette valeur avant de sélectionner un modèle de projet, car seuls les modèles compatibles avec cette version du .NET Framework s'affichent dans la liste.  

 Le .NET Framework 3.5 doit être installé sur votre système pour pouvoir accéder aux versions du Framework antérieures à 4.0.  

## <a name="download-sample-solutions"></a>Télécharger des exemples de solutions  
 Vous pouvez utiliser Visual Studio pour télécharger et installer des exemples de solutions à partir de [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=254185), ainsi qu’à partir d’autres sources, telles que des dépôts Git.

 Vous pouvez télécharger les exemples individuellement, ou vous pouvez télécharger un pack d'exemples, qui contient des exemples associés qui partagent une technologie ou une rubrique. Vous recevrez une notification lorsque des modifications du code source seront publiées pour tout exemple que vous téléchargez.  

 Pour plus d’informations, consultez [Exemples Visual Studio](../ide/visual-studio-samples.md).  

## <a name="add-single-files-at-the-solution-level"></a>Ajouter des fichiers uniques au niveau de la solution  
 Vous pouvez parfois avoir un fichier auquel plusieurs projets font référence, ou qui contient du texte ou des données diverses qui appartiennent logiquement au niveau de la solution plutôt qu’à un projet spécifique.  Pour ajouter un élément à une solution  

- Cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter**, **Nouvel élément** ou **Ajouter**, **Élément existant**.  

## <a name="create-empty-solutions"></a>Créer des solutions vides  
 Bien que les projets puissent résider dans une solution, vous pouvez également créer des solutions n’ayant aucun projet. Vous pouvez aussi ouvrir des projets de code sans avoir besoin d’une solution.

#### <a name="to-create-an-empty-solution"></a>Pour créer une solution vide  

1.  Dans le menu **Fichier**, choisissez **Nouveau**, **Nouveau projet**.  

2.  Dans le volet gauche, choisissez **Installé**, **Autres types de projets**, puis **Solutions Visual Studio** dans la liste développée.  

3.  Dans le volet du milieu, choisissez **Nouvelle Solution**.  

4.  Définissez les valeurs **Nom** et **Emplacement** de votre solution, puis choisissez **OK**.  

Après avoir créé une solution vide, vous pouvez lui ajouter des projets ou éléments nouveaux ou existants en choisissant **Ajouter un nouvel élément** ou **Ajouter un élément existant** dans le menu **Projet**.

### <a name="delete-solutions"></a>Supprimer des solutions  
 Vous pouvez supprimer définitivement une solution, mais pas à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Avant de supprimer une solution, déplacez les projets que vous pourriez vouloir réutiliser vers une autre solution. Utilisez ensuite l'Explorateur de fichiers pour supprimer le répertoire qui contient les fichiers solution .sln et .suo.  

> [!NOTE]
>  Le fichier .suo est un fichier masqué qui n'apparaît pas dans les paramètres par défaut de l'Explorateur de fichiers.  

##### <a name="to-delete-a-solution"></a>Pour supprimer une solution  

1.  Dans l’**Explorateur de solutions**, dans le menu contextuel (clic droit) de la solution à supprimer, choisissez **Ouvrir le dossier dans l’Explorateur de fichiers**.

2.  Dans l'Explorateur de fichiers, remontez d'un niveau.

3.  Choisissez le répertoire contenant la solution, puis appuyez sur la touche Suppr.

## <a name="see-also"></a>Voir aussi  
 [Projets et solutions](../ide/solutions-and-projects-in-visual-studio.md)   

