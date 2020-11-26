---
title: Utiliser la liste des tâches
description: Découvrez comment l’Liste des tâches dans Visual Studio peut vous aider à suivre et à utiliser des commentaires de code plus efficacement.
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d19794b4fce3e4a1388f864cecf408e0f7e9c53
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189834"
---
# <a name="use-the-task-list"></a>Utiliser la liste des tâches

Avec la **liste des tâches** , effectuez le suivi des commentaires de code qui utilisent des jetons tels que `TODO` et `HACK`, ou des jetons personnalisés, et gérez les raccourcis qui permettent d’accéder directement à un emplacement prédéfini dans le code. Cliquez sur l’élément dans la liste pour accéder à son emplacement dans le code source.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Commentaires de tâche (Visual Studio pour Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Fenêtre Liste des tâches

Quand la **Liste des tâches** est ouverte, elle apparaît en bas de la fenêtre d’application.

Pour ouvrir la **liste des tâches**, sélectionnez **Affichage** > **Liste des tâches** ou utilisez le raccourci clavier **Ctrl**+**\\**,**T**.

![Fenêtre Liste des tâches](../ide/media/vs2015_task_list.png)

Pour modifier l’ordre de tri de la liste, sélectionnez l’en-tête d’une colonne. Pour affiner vos résultats de recherche, appuyez sur **MAJ** et cliquez sur un deuxième en-tête de colonne. Comme alternative, dans le menu contextuel, vous pouvez sélectionner **Trier par**, puis choisir un en-tête. Pour affiner vos résultats de recherche, appuyez sur **Maj** et choisissez un deuxième en-tête.

Pour afficher ou masquer des colonnes, dans le menu contextuel, choisissez **Afficher les colonnes**. Sélectionnez les colonnes que vous souhaitez afficher ou masquer.

Pour modifier l’ordre des colonnes, faites glisser un en-tête de colonne vers l’emplacement souhaité.

## <a name="user-tasks"></a>Tâches de l’utilisateur

La fonctionnalité des tâches utilisateur n’est plus disponible dans Visual Studio 2015. Quand vous ouvrez une solution qui contient des données de tâches utilisateur ayant été créées dans Visual Studio 2013 ou une version antérieure, ces données sont conservées dans votre fichier *.suo*, mais les tâches utilisateur ne s’affichent pas dans la liste des tâches.

Si vous voulez continuer à accéder aux données de tâches utilisateur et les mettre à jour, ouvrez le projet dans Visual Studio 2013 et copiez le contenu de toutes les tâches utilisateur dans votre outil de gestion de projet par défaut (tel que Team Foundation Server).

## <a name="tokens-and-comments"></a>Jetons et commentaires

Un commentaire dans votre code, précédé d'un marqueur de commentaire et d'un jeton prédéfini, apparaît également dans **Liste des tâches**. Par exemple, le commentaire C# suivant comprend trois parties distinctes :

- le marqueur de commentaire (`//`) ;

- le jeton, par exemple (`TODO`) ;

- le commentaire (le reste du texte).

```csharp
// TODO: Load state from previously suspended application
```

Étant donné que `TODO` est un jeton prédéfini, ce commentaire s’affiche comme une tâche `TODO` dans la liste.

### <a name="custom-tokens"></a>Jetons personnalisés

Par défaut, Visual Studio inclut les jetons suivants : `HACK`, `TODO`, `UNDONE` et `UnresolvedMergeConflict`. Ils ne respectent pas la casse. Vous pouvez également créer vos propres jetons personnalisés.

> [!NOTE]
> Les jetons par défaut sont disponibles uniquement pour les langages C/C++, C# et VB. Pour créer vos propres jetons pour d’autres langages de programmation, procédez comme suit.

Pour créer un jeton personnalisé :

1. Dans le menu **Outils**, choisissez **Options**.

2. Ouvrez le dossier **Environnement** , puis choisissez **Liste des tâches**.

   La [page Options de la liste des tâches](../ide/reference/task-list-environment-options-dialog-box.md) s’affiche.

   ![Liste des tâches Visual Studio](../ide/media/vs2015_task_list_options.png)

3. Dans la zone de texte **Nom**, entrez le nom de votre jeton, par exemple **BOGUE**.

4. Dans la liste déroulante **Priorité** , choisissez une priorité par défaut pour le nouveau jeton.

5. Choisissez **Ajouter**.

> [!TIP]
> Le bouton **Ajouter** devient disponible dès que vous entrez un nom. Vous devez entrer un nom avant de cliquer sur **Ajouter**.

### <a name="c-todo-comments"></a>Commentaires TODO C++

Par défaut, les commentaires TODO C++ sont affichés dans **Liste des tâches**.

Pour désactiver les commentaires TODO C++, dans le menu **Outils**, choisissez **Options** > **Éditeur de texte** > **C/C++** > **Affichage** > **Énumérer les tâches de commentaire** et définissez la valeur sur **false**.

## <a name="shortcuts"></a>Raccourcis

Un *raccourci* est un signet dans le code qui est suivi dans la **liste des tâches**. Il comporte une icône différente de celle d’un signet normal. Double-cliquez sur le raccourci dans la fenêtre **Liste des tâches** pour accéder à l'emplacement correspondant dans le code.

![Icône de raccourci de la liste des tâches Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Créer un raccourci

Pour créer un raccourci, insérez le pointeur dans le code à l’emplacement souhaité du nouveau raccourci. Choisissez **modifier** les  >  **signets**  >  **Ajouter liste des tâches raccourci** ou appuyez sur **CTRL** + **K**, **CTRL** + **H**.

Pour parcourir les raccourcis figurant dans le code, choisissez un raccourci dans la liste, puis **Tâche suivante** ou **Tâche précédente** dans le menu contextuel.

## <a name="see-also"></a>Voir aussi

- [Liste des tâches, environnement, boîte de dialogue Options](../ide/reference/task-list-environment-options-dialog-box.md)
- [Commentaires de tâche (Visual Studio pour Mac)](/visualstudio/mac/task-comments)
