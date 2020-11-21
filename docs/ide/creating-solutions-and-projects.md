---
title: Créer des solutions et des projets
description: Découvrez la différence entre les solutions et les projets et comment les utiliser dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/06/2018
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd893c06da9bc2c2c8d95fc4c085affa815edd2
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006443"
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

## <a name="create-a-project-from-a-project-template"></a>Créer un projet à partir d'un modèle de projet

Pour plus d’informations sur la création d’un projet à partir d’un modèle, consultez [Créer un projet dans Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Créer un projet à partir de fichiers de code existants

Si vous avez déjà une collection de fichiers de code source, vous pouvez facilement les ajouter à un projet.

1. Dans le menu, choisissez **fichier**  >  **nouveau**  >  **projet à partir du code existant**.

1. Dans l’Assistant **Créer un projet à partir de fichiers de code existants**, choisissez le type de projet souhaité dans la zone de liste déroulante **Quel type de projet voulez-vous créer ?**, puis choisissez le bouton **Suivant**.

1. Dans l’Assistant, accédez à l’emplacement des fichiers, puis entrez le nom du nouveau projet dans la zone **Nom**. Quand vous avez terminé, choisissez le bouton **Terminer**.

> [!NOTE]
> Cette option est la plus appropriée pour une collection de fichiers relativement simple. Actuellement, seuls les types de projets C++, Apache Cordova, Visual Basic et C# sont pris en charge.

## <a name="add-files-to-a-solution"></a>Ajouter des fichiers à une solution

Si vous utilisez des fichiers qui s’appliquent à plusieurs projets, comme un fichier Lisezmoi pour la solution, ou d’autres fichiers qui sont logiquement associés à la solution globale plutôt qu’à un projet particulier, vous pouvez les ajouter directement à la solution. Pour ajouter un élément à une solution, dans le menu contextuel (clic droit) du nœud de solution dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Nouvel élément** ou **Ajouter** > **Élément existant**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Créer un projet .NET qui cible une version spécifique du .NET Framework

Quand vous créez un projet .NET Framework, vous pouvez spécifier une version spécifique du .NET Framework que votre projet doit utiliser. (Quand vous créez un projet .NET Core, vous ne spécifiez pas de version du framework.)

::: moniker range="vs-2017"

Pour spécifier une version du .NET Framework, choisissez le menu déroulant **Framework** dans la boîte de dialogue **Nouveau projet**.

![Liste déroulante Framework dans la boîte de dialogue Nouveau projet](./media/vside-newproject-framework.png)

> [!NOTE]
> Vous devez avoir .NET Framework 3.5 installé sur votre système pour pouvoir accéder aux versions de .NET Framework antérieures à .NET Framework 4.

::: moniker-end

::: moniker range=">=vs-2019"

Pour spécifier une version de .NET Framework, choisissez le menu déroulant **Framework** sur la page **créer un nouveau projet** .

![Sélecteur de framework dans la configuration d’un nouveau projet](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Créer des solutions vides

Vous pouvez également créer des solutions vides qui ne contiennent pas de projets. Utilisez plutôt cette méthode si vous souhaitez créer vous-même entièrement votre solution et vos projets.

### <a name="to-create-an-empty-solution"></a>Pour créer une solution vide

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

::: moniker range="vs-2017"

2. Dans le volet gauche (**Modèles**), choisissez **Autres types de projets** > **Solutions Visual Studio** dans la liste développée.

3. Dans le volet du milieu, choisissez **Nouvelle Solution**.

4. Entrez les valeurs **Nom** et **Emplacement** de votre solution, puis choisissez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la page **Créer un projet**, tapez **solution** dans la zone de recherche.

3. Sélectionnez le modèle **Solution vide**, puis cliquez sur **Suivant**.

4. Entrez les valeurs **Nom** et **Emplacement** pour votre solution, puis choisissez **Créer**.

::: moniker-end

Après avoir créé une solution vide, vous pouvez lui ajouter des projets ou éléments nouveaux ou existants en choisissant **Ajouter un nouvel élément** ou **Ajouter un élément existant** dans le menu **Projet**.

Comme mentionné plus haut, vous pouvez aussi ouvrir des fichiers de code sans avoir besoin d’un projet ou d’une solution. Pour en savoir plus sur le développement de code de cette façon, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Créer un projet temporaire

(C# et Visual Basic uniquement)

Si vous créez un projet .NET sans spécifier un emplacement sur disque, le projet est considéré comme temporaire. Les projets temporaires sont utiles pour faire des essais avec des projets .NET. Quand vous travaillez avec un projet temporaire, vous pouvez choisir de l’enregistrer ou de le supprimer à tout moment.

Pour créer un projet temporaire, accédez d’abord à **Outils**  >  **options**  >  **projets et solutions**  >  **général**, puis décochez la case **enregistrer les nouveaux projets lors** de leur création. Ouvrez ensuite la boîte de dialogue **Nouveau projet**.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Supprimer une solution, un projet ou un élément

Vous pouvez supprimer des solutions et tout leur contenu définitivement, mais cela n’est pas possible par le biais de l’IDE de Visual Studio. En effet, quand vous supprimez des éléments dans Visual Studio, les éléments sont supprimés uniquement dans la solution ou le projet actifs. Pour supprimer définitivement une solution ou un autre composant de votre système, vous devez supprimer le dossier contenant les fichiers solution *.sln* et *.suo* dans l’Explorateur de fichiers. Toutefois, avant de supprimer définitivement une solution, nous vous recommandons de sauvegarder les projets ou fichiers dont vous pourriez avoir besoin ultérieurement.

> [!NOTE]
> Le fichier *.suo* est un fichier masqué qui n’apparaît pas dans les paramètres par défaut de l’Explorateur de fichiers. Pour afficher les fichiers masqués, dans le menu **Affichage** de l’Explorateur de fichiers, cochez la case **Éléments masqués**.

### <a name="permanently-delete-a-solution"></a>Pour supprimer définitivement une solution

1. Dans **l’Explorateur de solutions**, choisissez **Ouvrir le dossier dans l’Explorateur de fichiers** dans le menu contextuel (clic droit) de la solution à supprimer.

1. Dans l'Explorateur de fichiers, remontez d'un niveau.

1. Choisissez le dossier contenant la solution, puis appuyez sur la touche **Suppr**.

## <a name="see-also"></a>Voir aussi

- [Solutions et projets](../ide/solutions-and-projects-in-visual-studio.md)
- [Référentiels open source de Microsoft sur GitHub](https://github.com/Microsoft)
- [Exemples de code pour développeurs](https://code.msdn.microsoft.com/)
- [Créer des projets (Visual Studio pour Mac)](/visualstudio/mac/create-new-projects)
