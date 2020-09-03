---
title: Création d'un projet
ms.date: 03/19/2019
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7cecf6a68296b3bffd07cca13fc3a3d0d5bc836
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770734"
---
# <a name="create-a-new-project-in-visual-studio"></a>Création d'un projet dans Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Ouvrir la boîte de dialogue Nouveau projet

Il existe plusieurs façons de créer un projet dans Visual Studio 2017. Dans la page Démarrage, entrez le nom d’un modèle de projet dans la zone **Rechercher dans les modèles de projet**, ou choisissez le lien **Créer un projet** pour ouvrir la boîte de dialogue **Nouveau projet**. À part la page de démarrage, vous pouvez également choisir **fichier**  >  **nouveau**  >  **projet** dans la barre de menus ou cliquer sur le bouton **nouveau projet** dans la barre d’outils.

![Page Démarrer et Fichier > Nouveau > Projet](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Sélectionner un type de modèle

Dans la boîte de dialogue **Nouveau projet**, les modèles de projet disponibles sont répertoriés sous la catégorie **Modèles**. Les modèles sont organisés par langage de programmation et type de projet, par exemple, Visual C#, JavaScript et Azure Data Lake.

![Boîte de dialogue Nouveau projet](./media/vside-newproject-templates-list.png)

> [!NOTE]
> La liste des langages de programmation et des modèles de projet disponibles dépend de la version de Visual Studio que vous utilisez et des charges de travail qui sont installées. Pour découvrir comment installer des charges de travail supplémentaires, consultez [Modifier Visual Studio en ajoutant ou supprimant des charges de travail et des composants](../install/modify-visual-studio.md).

Affichez la liste des modèles disponibles pour le langage de programmation souhaité en cliquant sur le triangle en regard du nom du langage, puis en choisissant une catégorie de projet (comme Windows Desktop).

L’image suivante montre les modèles de projet disponibles pour les projets .NET Core en Visual C# :

![Modèles de projet](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurer votre projet

Entrez le nom du nouveau projet dans la zone **Nom**. Vous pouvez enregistrer le projet à l’emplacement par défaut sur votre système ou bien cliquez sur le bouton **Parcourir** pour rechercher un autre emplacement. Vous pouvez également choisir un nom de solution ou ajouter le nouveau projet à un dépôt Git (en choisissant **Ajouter au contrôle de code source**).

Cliquez sur **OK** pour créer la solution et le projet.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Ouvrir la page Créer un projet

Il existe plusieurs façons de créer un projet dans Visual Studio 2019. Quand vous ouvrez Visual Studio pour la première fois, la fenêtre de démarrage s’affiche, et à partir de là, vous pouvez choisir **Créer un projet**.

![Créer un projet à partir de la fenêtre de démarrage dans Visual Studio 2019](media/vs-2019/start-window-create-new-project.png)

Si l’environnement de développement Visual Studio est déjà ouvert, vous pouvez créer un projet en choisissant **Fichier** > **Nouveau** > **Projet** dans la barre de menus ou en cliquant sur le bouton **Nouveau projet** dans la barre d’outils.

![Bouton Nouveau projet dans Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Sélectionner un type de modèle

Dans la page **Créer un projet**, une liste de vos modèles récemment sélectionnés s’affiche sur la gauche. Les modèles sont triés selon l’*utilisation la plus récente*.

Si vous ne faites pas votre sélection dans les modèles récemment utilisés, vous pouvez filtrer tous les modèles de projet disponibles par **Langage** (par exemple C# ou C++), par **Plateforme** (par exemple Windows ou Azure) et par **Type de projet** (par exemple Desktop ou Web). Vous pouvez aussi entrer un texte à rechercher dans la zone de recherche pour filtrer encore davantage les modèles, par exemple **asp.net**.

![Filtres de modèle de projet dans Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

Les étiquettes qui apparaissent sous chaque modèle correspondent aux trois filtres de liste déroulante (Langage, Plateforme et Type de projet).

> [!TIP]
> Si vous ne voyez pas le modèle que vous recherchez, il vous manque peut-être une charge de travail pour Visual Studio. Pour installer des charges de travail supplémentaires, par exemple **Développement Azure** ou **Développement mobile en .NET**, cliquez sur le lien **Installer d’autres outils et fonctionnalités** pour ouvrir Visual Studio Installer. À partir de là, sélectionnez les charges de travail que vous voulez installer, puis choisissez **Modifier**. Après cela, les modèles de projet supplémentaires seront disponibles.
>
> ![Lien Installer plus d’outils et de fonctionnalités dans Visual Studio 2019](media/vs-2019/install-more-tools-features.png)

Sélectionnez un modèle, puis cliquez **Suivant**.

## <a name="configure-your-project"></a>Configurer votre projet

La page **Configurer votre nouveau projet** a des options permettant de nommer votre projet (et la solution), de choisir un emplacement sur le disque et de sélectionner une version du Framework (si cela s’applique au modèle que vous avez choisi).

![Page Configurer votre nouveau projet dans Visual Studio 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Si vous créez un projet alors qu’une solution ou un projet est déjà ouvert dans Visual Studio, une option de configuration supplémentaire est disponible. Vous pouvez choisir de créer une solution ou d’ajouter le nouveau projet à la solution qui est déjà ouverte.
>
> ![Créer une solution ou ajouter à une solution existante dans Visual Studio 2019](media/vs-2019/configure-new-project-solution.png)

Cliquez sur **Créer** pour créer le projet.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Ajouter des projets supplémentaires à une solution

Si vous voulez ajouter un projet supplémentaire à une solution, cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

## <a name="see-also"></a>Voir aussi

- [Créer des solutions et des projets](creating-solutions-and-projects.md)
