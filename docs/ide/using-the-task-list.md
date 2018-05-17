---
title: Utiliser la liste des tâches
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a82663fe397488ee78a82d4fab5d38bfec4ae37
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="use-the-task-list"></a>Utiliser la liste des tâches

Avec la **liste des tâches** , effectuez le suivi des commentaires de code qui utilisent des jetons tels que `TODO` et `HACK`, ou des jetons personnalisés, et gérez les raccourcis qui permettent d’accéder directement à un emplacement prédéfini dans le code. Cliquez sur l’élément dans la liste pour accéder à son emplacement dans le code source.

## <a name="the-task-list-window"></a>Fenêtre Liste des tâches

Quand la **Liste des tâches** est ouverte, elle apparaît en bas de la fenêtre d’application.

### <a name="open-the-task-list"></a>Ouvrir la Liste des tâches

- Dans le menu **Affichage**, choisissez **Liste des tâches** (clavier : **Ctrl**+**\\**,**T**).

    ![Fenêtre Liste des tâches](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="change-the-sort-order-of-the-list"></a>Changer l’ordre de tri de la liste

- Cliquez sur l'en-tête d'une colonne quelconque. Pour affiner vos résultats de recherche, appuyez sur Maj et cliquez sur un deuxième en-tête de colonne.

     Comme alternative, dans le menu contextuel, vous pouvez choisir **Trier par**, puis choisir un en-tête. Pour affiner vos résultats de recherche, appuyez sur **Maj** et choisissez un deuxième en-tête.

### <a name="show-or-hide-columns"></a>Afficher ou masquer des colonnes

- Dans le menu contextuel, choisissez **Afficher les colonnes**. Choisissez les colonnes que vous souhaitez afficher ou masquer.

### <a name="change-the-order-of-the-columns"></a>Changer l’ordre des colonnes

- Faites glisser n'importe quel en-tête de colonne à l'emplacement de votre choix.

## <a name="user-tasks"></a>Tâches utilisateur

La fonctionnalité des tâches utilisateur n’est plus disponible depuis Visual Studio 2015. Quand vous ouvrez une solution qui contient des données de tâches utilisateur ayant été créées dans Visual Studio 2013 ou une version antérieure, ces données sont conservées dans votre fichier *.suo*, mais les tâches utilisateur ne s’affichent pas dans la liste des tâches.

Si vous voulez continuer à accéder aux données de tâches utilisateur et les mettre à jour, vous devez ouvrir le projet dans Visual Studio 2013 et copier le contenu de toutes les tâches utilisateur dans votre outil de gestion de projet par défaut (tel que Team Foundation Server).

## <a name="tokens-and-comments"></a>Jetons et commentaires

Un commentaire dans votre code, précédé d'un marqueur de commentaire et d'un jeton prédéfini, apparaîtra également dans la fenêtre **Liste des tâches** . Par exemple, le commentaire C# suivant comprend trois parties distinctes :

- le marqueur de commentaire (`//`) ;

- le jeton, par exemple (`TODO`) ;

- le commentaire (le reste du texte).

```csharp
// TODO: Load state from previously suspended application
```

Étant donné que `TODO` est un jeton prédéfini, ce commentaire s’affiche comme une tâche `TODO` dans la liste.

###  <a name="customTokens"></a> Jetons personnalisés

Par défaut, Visual Studio inclut les jetons suivants : `HACK`, `TODO`, `UNDONE`, `NOTE`. Ces jetons ne respectent pas la casse.

Vous pouvez également créer vos propres jetons personnalisés.

#### <a name="create-a-custom-token"></a>Créer un jeton personnalisé

1. Dans le menu **Outils** , choisissez **Options**.

2. Ouvrez le dossier **Environnement** , puis choisissez **Liste des tâches**.

     La [page Options de la liste des tâches](../ide/reference/task-list-environment-options-dialog-box.md) s’affiche.

     ![Liste des tâches Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. Dans la catégorie **Jetons** , dans la zone de texte **Nom** , entrez le nom du jeton, par exemple « BOGUE ».

4. Dans la liste déroulante **Priorité** , choisissez une priorité par défaut pour le nouveau jeton. Choisissez le bouton **Ajouter** .

###  <a name="cppComments"></a> Commentaires TODO C++

Par défaut, les commentaires TODO C++ sont affichés dans la fenêtre **Liste des tâches** . Vous pouvez modifier ce comportement.

#### <a name="turn-off-c-todo-comments"></a>Désactiver les commentaires TODO C++

Dans le menu **Outils**, choisissez **Options** > **Éditeur de texte** > **C/C++** > **Affichage** > **Énumérer les tâches de commentaire** et définissez la valeur sur false.

## <a name="shortcuts"></a>Raccourcis

Un *raccourci* est un signet dans le code qui est suivi dans la **Liste des tâches**; son icône est différente de celle d’un signet normal. Double-cliquez sur le raccourci dans la fenêtre **Liste des tâches** pour accéder à l'emplacement correspondant dans le code.

![Icône de raccourci de la liste des tâches Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="create-a-shortcut"></a>Créer un raccourci

Pour créer un raccourci, insérez le pointeur dans le code à l’emplacement souhaité du nouveau raccourci. Choisissez **Edition** > **Signets** > **Ajouter un raccourci vers la liste des tâches** ou appuyez sur **Ctrl** + **K**, **Ctrl**+**H**.

Pour parcourir les raccourcis figurant dans le code, choisissez un raccourci dans la liste, puis **Tâche suivante** ou **Tâche précédente** dans le menu contextuel.

## <a name="see-also"></a>Voir aussi

- [Liste des tâches, Environnement, boîte de dialogue Options](../ide/reference/task-list-environment-options-dialog-box.md)