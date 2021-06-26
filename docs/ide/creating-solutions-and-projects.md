---
title: Créer & utiliser des projets Visual Studio & des solutions
description: Découvrez la différence entre les solutions et les projets et comment les utiliser dans Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 713d320767bd329cc53b536bdad058a5db592b3f
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924927"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Créer, utiliser et supprimer des projets et solutions Visual Studio

Dans cet article, vous allez apprendre à créer et à utiliser des projets Visual Studio à partir de zéro pour stocker les artefacts dont vous avez besoin pour générer vos applications.  Si vous n’êtes pas familiarisé avec les projets dans Visual Studio, consultez cette vue d’ensemble des [projets et des solutions](solutions-and-projects-in-visual-studio.md).  Pour savoir comment créer rapidement un projet à partir d’un modèle, consultez [créer un projet à partir d’un modèle](create-new-project.md).

Les *projets* regroupent tous les éléments dont vous avez besoin pour générer votre application dans Visual Studio, tels que les fichiers de code source, les bitmaps, les icônes, et les références de composant et de service. Quand vous créez un projet, Visual Studio crée une *solution* dans laquelle est placé votre projet. Vous pouvez ensuite ajouter d’autres projets nouveaux ou existants à la solution. Les solutions peuvent également contenir des fichiers qui ne sont pas associés à un projet spécifique.

![Diagramme montrant la hiérarchie de la solution et du projet.](./media/vside-proj-soln.png)

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Créer des projets dans Visual Studio pour Mac](/visualstudio/mac/create-new-projects).

Vous pouvez afficher vos solutions et projets dans une fenêtre Outil appelée **Explorateur de solutions**. La capture d’écran suivante montre un exemple de solution dans l’**Explorateur de solutions** (**BikeSharing.Xamarin-UWP**), qui contient deux projets : **BikeSharing.Clients.Core** et **BikeSharing.Clients.Windows**. Chaque projet contient plusieurs fichiers, dossiers et références. Le nom du projet en gras est le *projet de démarrage*, c’est-à-dire le projet qui démarre quand vous exécutez l’application. Vous pouvez spécifier le projet à utiliser comme projet de démarrage.

![Capture d’écran de Explorateur de solutions avec deux projets.](./media/vside-solution-explorer-projects.png)

Vous pouvez créer un projet vous-même en y ajoutant les fichiers nécessaires ou créer un projet à partir d’un des modèles de projet disponibles dans Visual Studio. Quand vous créez un projet à partir d’un modèle, votre projet contient les éléments essentiels pour le type de projet choisi. Vous pouvez ensuite renommer les fichiers et ajouter du code nouveau ou existant et d’autres ressources selon vos besoins.

Cela étant dit, le développement d’applications dans Visual Studio peut se faire sans solutions ni projets. Vous pouvez simplement ouvrir du code que vous avez cloné à partir de Git ou téléchargé d’une source de votre choix. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Créer un projet à partir d'un modèle de projet

Pour plus d’informations sur la façon de sélectionner un modèle pour créer un projet, consultez [créer un nouveau projet dans Visual Studio](create-new-project.md). Et, pour obtenir un exemple d’un projet et d’une solution créés à partir de zéro, avec des instructions pas à pas et des exemples de code, consultez [Présentation des projets et des solutions](../get-started/tutorial-projects-solutions.md).

## <a name="create-a-project-from-existing-code-files"></a>Créer un projet à partir de fichiers de code existants

Si vous avez déjà une collection de fichiers de code source, vous pouvez facilement les ajouter à un projet.

1. Dans le menu, sélectionnez **fichier**  >  **nouveau**  >  **projet à partir du code existant**.

1. Dans l’Assistant **créer un projet à partir de fichiers de code existants** , sélectionnez le type de projet que vous souhaitez dans la zone de liste déroulante **quel type de projet voulez-vous créer ?** , puis sélectionnez le bouton **suivant** .

1. Dans l’Assistant, accédez à l’emplacement des fichiers, puis entrez le nom du nouveau projet dans la zone **Nom**. Lorsque vous avez terminé, sélectionnez le bouton **Terminer** .

> [!NOTE]
> Cette option est la plus appropriée pour une collection de fichiers relativement simple. Actuellement, seuls les types de projets C++, Apache Cordova, Visual Basic et C# sont pris en charge.

## <a name="add-files-to-a-solution"></a>Ajouter des fichiers à une solution

Si vous utilisez des fichiers qui s’appliquent à plusieurs projets, comme un fichier Lisezmoi pour la solution, ou d’autres fichiers qui sont logiquement associés à la solution globale plutôt qu’à un projet particulier, vous pouvez les ajouter directement à la solution. Pour ajouter un élément à une solution, dans le menu contextuel (clic droit) du nœud de la solution dans **Explorateur de solutions**, sélectionnez **Ajouter** un  >  **nouvel élément** ou **Ajouter** un  >  **élément existant**.

> [!TIP]
> Un fichier solution est une structure d’organisation des projets dans Visual Studio. Elle contient l’état de ces informations dans deux fichiers : un fichier *. sln* (texte, partagé) et un fichier *. suo* (fichiers binaires, masqués, spécifiques à l’utilisateur). Par conséquent, une solution n’est pas une solution qui doit être copiée et renommée ; au lieu de cela, il est préférable de créer une solution, puis d’y ajouter des éléments existants.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Créer un projet .NET qui cible une version spécifique du .NET Framework

Quand vous créez un projet .NET Framework, vous pouvez spécifier une version spécifique du .NET Framework que votre projet doit utiliser. (Quand vous créez un projet .NET Core, vous ne spécifiez pas de version du framework.)

::: moniker range="vs-2017"

Pour spécifier une version de .NET Framework, sélectionnez le menu déroulant **Framework** dans la boîte de dialogue **nouveau projet** .

![Capture d’écran de la liste déroulante Framework dans la boîte de dialogue Nouveau projet.](./media/vside-newproject-framework.png)

> [!NOTE]
> Vous devez avoir .NET Framework 3.5 installé sur votre système pour pouvoir accéder aux versions de .NET Framework antérieures à .NET Framework 4.

::: moniker-end

::: moniker range=">=vs-2019"

Pour spécifier une version de .NET Framework, sélectionnez le menu déroulant **Framework** sur la page **créer un nouveau projet** .

![Capture d’écran du sélecteur d’infrastructure dans la boîte de dialogue « Configurer un nouveau projet ».](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Créer des solutions vides

Vous pouvez également créer des solutions vides qui ne contiennent pas de projets. Utilisez plutôt cette méthode si vous souhaitez créer vous-même entièrement votre solution et vos projets.

### <a name="to-create-an-empty-solution"></a>Pour créer une solution vide

1. Dans la barre de menus, sélectionnez **fichier**  >  **nouveau**  >  **projet**.

::: moniker range="vs-2017"

2. Dans le volet gauche (**modèles**), sélectionnez **autres types de projets** > **solutions Visual Studio** dans la liste développée.

3. Dans le volet central, sélectionnez **Nouvelle Solution**.

4. Entrez les valeurs **nom** et **emplacement** de votre solution, puis sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la page **Créer un projet**, tapez **solution** dans la zone de recherche.

3. Sélectionnez le modèle **Solution vide**, puis cliquez sur **Suivant**.

4. Entrez les valeurs **nom** et **emplacement** de votre solution, puis sélectionnez **créer**.

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

Vous pouvez utiliser le menu contextuel en cliquant avec le bouton droit pour supprimer ou supprimer des solutions, des projets ou des éléments dans Visual Studio, mais qui les supprime uniquement de la solution ou du projet actuel.

Pour supprimer définitivement une solution ou d’autres composants de votre système, utilisez l' **Explorateur de fichiers** dans Windows pour supprimer le dossier qui contient les fichiers solution *. sln* et *. suo* . (Avant de supprimer une solution, vous souhaiterez peut-être sauvegarder vos projets et vos fichiers si vous en avez besoin de nouveau.)

> [!NOTE]
> Le fichier *. suo* est un fichier masqué qui n’est pas affiché sous les paramètres par défaut de l’Explorateur de fichiers. Pour afficher les fichiers masqués, dans le menu **Affichage** de l’Explorateur de fichiers, cochez la case **Éléments masqués**.

### <a name="permanently-delete-a-solution"></a>Pour supprimer définitivement une solution

Vous pouvez accéder à l’Explorateur de fichiers dans Windows à l’aide de Explorateur de solutions dans Visual Studio. Voici comment procéder.

1. Dans **Explorateur de solutions**, dans le menu contextuel (menu contextuel) de la solution que vous souhaitez supprimer, sélectionnez **ouvrir le dossier dans l’Explorateur de fichiers**.

1. Dans l'Explorateur de fichiers, remontez d'un niveau.

1. Sélectionnez le dossier qui contient la solution, puis appuyez sur la touche **Suppr** .

## <a name="see-also"></a>Voir aussi

- [Présentation des projets et solutions](../get-started/tutorial-projects-solutions.md)
- [Gérer les propriétés des projets et des solutions](managing-project-and-solution-properties.md)
- [Solutions filtrées dans Visual Studio](filtered-solutions.md)
- [Référentiels open source de Microsoft sur GitHub](https://github.com/Microsoft)
- [Exemples de code pour développeurs](https://code.msdn.microsoft.com/)
- [Ressources pour la résolution des erreurs de l’IDE Visual Studio](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
