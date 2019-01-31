---
title: Créer des solutions et des projets
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eba7b2a54b2f883dddff02a17cb6bc666869ec24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025109"
---
# <a name="create-solutions-and-projects"></a>Créer des solutions et des projets

Les *projets* regroupent tous les éléments dont vous avez besoin pour générer votre application dans Visual Studio, tels que les fichiers de code source, les bitmaps, les icônes, et les références de composant et de service. Quand vous créez un projet, Visual Studio crée une *solution* dans laquelle est placé votre projet. Vous pouvez ensuite ajouter d’autres projets nouveaux ou existants à la solution. Les solutions peuvent également contenir des fichiers qui ne sont pas associés à un projet spécifique.

![Hiérarchie de projet/solution](./media/vside-proj-soln.png)

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Créer des projets dans Visual Studio pour Mac](/visualstudio/mac/create-new-projects).

Vous pouvez afficher vos solutions et projets dans une fenêtre Outil appelée **Explorateur de solutions**. La capture d’écran suivante montre un exemple de solution dans l’**Explorateur de solutions** (**BikeSharing.Xamarin-UWP**), qui contient deux projets : **BikeSharing.Clients.Core** et **BikeSharing.Clients.Windows**. Chaque projet contient plusieurs fichiers, dossiers et références. Le nom du projet en gras est le *projet de démarrage*, c’est-à-dire le projet qui démarre quand vous exécutez l’application. Vous pouvez spécifier le projet à utiliser comme projet de démarrage.

![Explorateur de solutions avec des projets](./media/vside-solution-explorer-projects.png)

Vous pouvez créer un projet vous-même en y ajoutant les fichiers nécessaires ou créer un projet à partir d’un des modèles de projet disponibles dans Visual Studio. Quand vous créez un projet à partir d’un modèle, votre projet contient les éléments essentiels pour le type de projet choisi. Vous pouvez ensuite renommer les fichiers et ajouter du code nouveau ou existant et d’autres ressources selon vos besoins.

Cela étant dit, le développement d’applications dans Visual Studio peut se faire sans solutions ni projets. Vous pouvez simplement ouvrir du code que vous avez cloné à partir de Git ou téléchargé d’une source de votre choix. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Les descriptions de cette rubrique sont basées sur l'édition Visual Studio Community. Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites ici, selon vos paramètres ou votre version de Visual Studio. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

## <a name="to-create-a-project-from-a-project-template"></a>Pour créer un projet à partir d’un modèle de projet

1. Il existe plusieurs façons de créer un projet dans Visual Studio. Dans la **Page de démarrage**, entrez le nom d’un modèle de projet dans la zone **Rechercher dans les modèles de projet**, ou choisissez le lien **Créer un projet** pour ouvrir la boîte de dialogue **Nouveau projet**. Vous pouvez également choisir **Fichier** > **Nouveau** > **Projet** dans la barre de menus ou le bouton **Nouveau projet** dans la barre d’outils.

   ![Page de démarrage](./media/vside-newproject1.png)

   Dans la boîte de dialogue **Nouveau projet**, les modèles de projet disponibles sont répertoriés sous la catégorie **Modèles**. Les modèles sont organisés par langage de programmation et type de projet, par exemple, Visual C#, JavaScript et Azure Data Lake.

   ![Nouveau projet, boîte de dialogue](./media/vside-newproject-templates-list.png)

   > [!NOTE]
   > La liste des langages de programmation et des modèles de projet disponibles dépend de la version de Visual Studio que vous utilisez et des charges de travail qui sont installées. Pour découvrir comment installer des charges de travail supplémentaires, consultez [Modifier Visual Studio 2017 en ajoutant ou supprimant des charges de travail et des composants](../install/modify-visual-studio.md).

2. Affichez la liste des modèles disponibles pour le langage de programmation souhaité en choisissant la flèche à côté du nom du langage, puis en choisissant un type de projet.

   L’exemple suivant montre les modèles de projet disponibles pour des projets .NET Core Visual C#.

   ![Modèles de projet](./media/new-project-dialog-net-core.png)

3. Entrez le nom du nouveau projet dans la zone **Nom**. Vous pouvez enregistrer le projet à l’emplacement par défaut sur votre système, ou choisir le bouton **Parcourir** pour rechercher un autre emplacement.

   Vous pouvez également choisir de changer le nom de la solution, ou d’ajouter le nouveau projet à un référentiel Git en choisissant **Ajouter au contrôle de code source**.

4. Choisissez le bouton **OK** pour créer la solution et le projet.

5. Si vous souhaitez ajouter un projet supplémentaire à la solution, choisissez le nœud de la solution dans l’**Explorateur de solutions** puis, dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

## <a name="create-a-project-from-existing-code-files"></a>Créer un projet à partir de fichiers de code existants

Si vous avez déjà une collection de fichiers de code source, vous pouvez facilement les ajouter à un projet.

1. Dans le menu, choisissez **Fichier** > **Nouveau** >  **Projet à partir de code existant**.

1. Dans l’Assistant **Créer un projet à partir de fichiers de code existants**, choisissez le type de projet souhaité dans la zone de liste déroulante **Quel type de projet voulez-vous créer ?**, puis choisissez le bouton **Suivant**.

1. Dans l’Assistant, accédez à l’emplacement des fichiers, puis entrez le nom du nouveau projet dans la zone **Nom**. Quand vous avez terminé, choisissez le bouton **Terminer**.

> [!NOTE]
> Cette option est la plus appropriée pour une collection de fichiers relativement simple. Actuellement, seuls les types de projet Visual C++, Apache Cordova, Visual Basic et C# sont pris en charge.

## <a name="add-files-to-a-solution"></a>Ajouter des fichiers à une solution

Si vous utilisez des fichiers qui s’appliquent à plusieurs projets, comme un fichier Lisezmoi pour la solution, ou d’autres fichiers qui sont logiquement associés à la solution globale plutôt qu’à un projet particulier, vous pouvez les ajouter directement à la solution. Pour ajouter un élément à une solution, dans le menu contextuel (clic droit) du nœud de solution dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Nouvel élément** ou **Ajouter** > **Élément existant**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Créer un projet .NET qui cible une version spécifique du .NET Framework

Quand vous créez un projet, vous pouvez spécifier une version spécifique de .NET Framework à utiliser pour votre projet. Pour spécifier une version de .NET Framework, choisissez le menu déroulant **Framework** dans la boîte de dialogue **Nouveau projet**.

![Liste déroulante Framework dans la boîte de dialogue Nouveau projet](./media/vside-newproject-framework.png)

> [!NOTE]
> Vous devez avoir .NET Framework 3.5 installé sur votre système pour pouvoir accéder aux versions de .NET Framework antérieures à .NET Framework 4.

## <a name="create-empty-solutions"></a>Créer des solutions vides

Vous pouvez également créer des solutions vides qui ne contiennent pas de projets. Utilisez plutôt cette méthode si vous souhaitez créer vous-même entièrement votre solution et vos projets.

### <a name="to-create-an-empty-solution"></a>Pour créer une solution vide

1. Dans le menu, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet (**Modèles**) de gauche, choisissez **Autres types de projets** > **Solutions Visual Studio dans la liste développée**.

1. Dans le volet du milieu, choisissez **Nouvelle Solution**.

1. Entrez les valeurs **Nom** et **Emplacement** de votre solution, puis choisissez **OK**.

Après avoir créé une solution vide, vous pouvez lui ajouter des projets ou éléments nouveaux ou existants en choisissant **Ajouter un nouvel élément** ou **Ajouter un élément existant** dans le menu **Projet**.

Comme mentionné plus haut, vous pouvez aussi ouvrir des fichiers de code sans avoir besoin d’un projet ou d’une solution. Pour en savoir plus sur le développement de code de cette façon, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Créer un projet temporaire (C# et Visual Basic)

Si vous créez un projet .NET sans spécifier un emplacement sur disque, le projet est considéré comme temporaire. Les projets temporaires sont utiles pour faire des essais avec des projets .NET. Quand vous travaillez avec un projet temporaire, vous pouvez choisir de l’enregistrer ou de le supprimer à tout moment.

Pour créer un projet temporaire, accédez d’abord à **Outils** > **Options** > **Projets et solutions** > **Général** et désélectionnez la case **Enregistrer les nouveaux projets lors de la création**. Ouvrez ensuite la boîte de dialogue **Nouveau projet**.

## <a name="delete-a-solution-project-or-item"></a>Supprimer une solution, un projet ou un élément

Vous pouvez supprimer des solutions et tout leur contenu définitivement, mais cela n’est pas possible par le biais de l’IDE de Visual Studio. En effet, quand vous supprimez des éléments dans Visual Studio, les éléments sont supprimés uniquement dans la solution ou le projet actifs. Pour supprimer définitivement une solution ou un autre composant de votre système, vous devez supprimer le dossier contenant les fichiers solution *.sln* et *.suo* dans l’Explorateur de fichiers. Toutefois, avant de supprimer définitivement une solution, nous vous recommandons de sauvegarder les projets ou fichiers dont vous pourriez avoir besoin ultérieurement.

> [!NOTE]
> Le fichier *.suo* est un fichier masqué qui n’apparaît pas dans les paramètres par défaut de l’Explorateur de fichiers. Pour afficher les fichiers masqués, dans le menu **Affichage** de l’Explorateur de fichiers, cochez la case **Éléments masqués**.

### <a name="to-permanently-delete-a-solution"></a>Pour supprimer définitivement une solution

1. Dans **l’Explorateur de solutions**, choisissez **Ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel (clic droit) de la solution à supprimer.

1. Dans l'Explorateur de fichiers, remontez d'un niveau.

1. Choisissez le dossier contenant la solution, puis choisissez la touche **Suppr**.

## <a name="see-also"></a>Voir aussi

- [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
- [Référentiels open source de Microsoft sur GitHub](https://github.com/Microsoft)
- [Exemples de code pour développeurs](https://code.msdn.microsoft.com/)
- [Créer des projets (Visual Studio pour Mac)](/visualstudio/mac/create-new-projects)