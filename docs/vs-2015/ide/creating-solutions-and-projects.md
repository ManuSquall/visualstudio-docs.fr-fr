---
title: Création de projets et de solutions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03ecd3fcc253f255afc59c2d6412f3864fe253b8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300596"
---
# <a name="creating-solutions-and-projects"></a>Création de projets et de solutions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les projets sont les conteneurs logiques pour tout ce qui est nécessaire pour générer votre application. Quand vous créez un projet en choisissant **Fichier &#124; Nouveau &#124; Projet** dans le menu principal, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crée une solution pour le contenir. Vous pouvez ensuite si nécessaire ajouter plusieurs projets nouveaux ou existants à la solution. Vous pouvez créer des projets à partir de fichiers de code existants et vous pouvez créer des projets temporaires (.NET uniquement) qui sont supprimés quand vous en avez terminé avec eux.

> [!NOTE]
> Les descriptions de cette rubrique sont basées sur l'édition Visual Studio Community. Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites ici, selon vos paramètres ou votre version de Visual Studio. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-project-from-an-installed-project-template"></a>Créer un projet à partir d'un modèle de projet installé
 **Fichier &#124; Nouveau &#124; Projet** dans le menu principal pour afficher la boîte de dialogue Nouveau projet. Dans le volet gauche sous **Installé &#124; Modèles**, choisissez le langage de programmation, et la plateforme ou la technologie, puis choisissez parmi les modèles disponibles dans le volet central.

 Dans la boîte de dialogue **Nouveau projet** , la liste déroulante **Solution** vous permet de créer le projet dans une solution nouvelle ou existante, ou dans une nouvelle instance de Visual Studio.

## <a name="create-a-project-from-existing-code-files"></a>Créer un projet à partir de fichiers de code existants
 Si vous avez une collection de fichiers non intégrés, vous pouvez facilement créer un projet qui les contient. Choisissez **Fichier &#124; Nouveau &#124; Projet à partir de code existant** pour démarrer l’**Assistant Créer un projet à partir de fichiers de code existants** et suivez les invites.

> [!TIP]
> Cette option convient le mieux pour les collections de fichiers relativement simples.

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Créer un projet temporaire (C# et Visual Basic)
 En travaillant avec des projets temporaires, vous pouvez créer et expérimenter un projet .NET sans spécifier un emplacement sur le disque. Quand vous créez un projet, vous sélectionnez simplement un type et un modèle de projet, et vous spécifiez un nom dans la boîte de dialogue **Nouveau projet** . Pendant que vous travaillez avec le projet temporaire, vous pouvez à tout moment l'enregistrer ou vous pouvez l'abandonner.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Créer un projet .NET qui cible une version spécifique du .NET Framework
 Vous pouvez créer un projet pour cibler des versions antérieures du .NET Framework en utilisant le menu déroulant de la version du **.Net Framework** en haut de la boîte de dialogue **Nouveau projet** . Définissez cette valeur avant de sélectionner un modèle de projet, car seuls les modèles compatibles avec cette version du .NET Framework s'affichent dans la liste.

 Le .NET Framework 3.5 doit être installé sur votre système pour pouvoir accéder aux versions du Framework antérieures à 4.0.

## <a name="downloading-sample-solutions"></a>Téléchargement d'exemples de solutions
 Vous pouvez utiliser Visual Studio pour télécharger et installer des exemples de solutions depuis [MSDN Code Gallery](https://go.microsoft.com/fwlink/?LinkId=254185).

 Vous pouvez télécharger les exemples individuellement, ou vous pouvez télécharger un pack d'exemples, qui contient des exemples associés qui partagent une technologie ou une rubrique. Vous recevrez une notification lorsque des modifications du code source seront publiées pour tout exemple que vous téléchargez.

 Pour plus d’informations, consultez [Exemples Visual Studio](../ide/visual-studio-samples.md).

## <a name="adding-single-files-at-the-solution-level"></a>Ajout de fichiers uniques au niveau de la solution
 Vous pouvez parfois avoir un fichier auquel plusieurs projets font référence, ou qui contient du texte ou des données diverses qui appartiennent logiquement au niveau de la solution plutôt qu’à un projet spécifique.  Pour ajouter un élément à une solution

1. Cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions** et choisissez **Ajouter &#124; Nouvel élément** ou **Ajouter &#124; Élément existant**.

## <a name="creating-empty-solutions"></a>Création de solutions vides
 Bien qu'un projet doive résider dans une solution, vous pouvez créer une solution qui n'a aucun projet.

#### <a name="to-create-an-empty-solution"></a>Pour créer une solution vide

1. Dans le menu **Fichier** , cliquez sur **Nouveau** , puis cliquez sur **Nouveau projet**.

2. Dans le volet gauche, sélectionnez **Installé**, **Autres types de projets**, puis **Solutions Visual Studio** dans la liste développée.

3. Dans le volet central, sélectionnez **Nouvelle Solution**.

4. Définissez les valeurs **Nom** et **Emplacement** de votre solution, puis cliquez sur **OK**.

   Après avoir créé une solution vide, vous pouvez lui ajouter des projets ou éléments nouveaux ou existants en cliquant sur **Ajouter un nouvel élément** ou **Ajouter un élément existant** dans le menu **Projet** .

### <a name="deleting-solutions"></a>Suppression de solutions
 Vous pouvez supprimer définitivement une solution, mais pas à l'aide de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Avant de supprimer une solution, déplacez les projets que vous pourriez vouloir réutiliser vers une autre solution. Utilisez ensuite l'Explorateur de fichiers pour supprimer le répertoire qui contient les fichiers solution .sln et .suo.

> [!NOTE]
> Le fichier .suo est un fichier masqué qui n'apparaît pas dans les paramètres par défaut de l'Explorateur de fichiers.

##### <a name="to-delete-a-solution"></a>Pour supprimer une solution

1. Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur la solution à supprimer, puis sélectionnez **Ouvrir le dossier dans l'Explorateur de fichiers**.

2. Dans l'Explorateur de fichiers, remontez d'un niveau.

3. Sélectionnez le répertoire contenant la solution et appuyez sur Suppr.

## <a name="see-also"></a>Voir aussi
 [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md) [plume Comment : créer des solutions à projets multiples](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
