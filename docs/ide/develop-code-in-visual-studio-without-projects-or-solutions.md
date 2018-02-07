---
title: "Développer du code dans Visual Studio sans projets ni solutions | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40995be9ee5d5da5a3219dd8badcb13e4b3f6e62
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Développer du code dans Visual Studio sans projets ni solutions

Visual Studio 2017 permet d’ouvrir du code à partir de presque n’importe quel type de projet basé sur un répertoire dans Visual Studio sans avoir recours à un fichier solution ou de projet. Cela signifie que vous pouvez, par exemple, rechercher un projet de code sur Git, le cloner, puis l’ouvrir directement dans Visual Studio et commencer à développer sans avoir à créer de solution ou de projet.  

Non seulement vous modifiez le code et le générer dans Visual Studio, mais vous pouvez également naviguer dans votre code (comme vous le feriez avec la commande de navigation). Le code apparaît avec colorisation de la syntaxe et, dans de nombreux cas, comprend la saisie semi-automatique des instructions de base et le débogage, avec des points d’arrêt. Certains langages comprennent encore plus de fonctionnalités. Consultez [Créer des paramètres d’éditeur personnalisés et portables](create-portable-custom-editor-options.md) pour plus d’informations.  

## <a name="open-code-anywhere"></a>Ouvrez du code n’importe où

Vous pouvez ouvrir du code dans Visual Studio de différentes façons :  

- Dans la barre de menus de Visual Studio, choisissez **Fichier**, **Ouvrir**, **Dossier**, puis accédez à l’emplacement du code.  

- Dans le menu contextuel (clic droit) d’un dossier contenant le code, choisissez la commande **Ouvrir dans Visual Studio**.  

- Choisissez le lien **Ouvrir le dossier** lien sur la page de démarrage de Visual Studio.  

- Ouvrez le code cloné à partir d’un référentiel GitHub.  

### <a name="to-open-code-from-a-cloned-github-repo"></a>Pour ouvrir du code à partir d’un référentiel GitHub cloné

L’exemple suivant montre comment cloner un référentiel GitHub, puis ouvrir son code dans Visual Studio. Pour suivre cette procédure, vous devez disposer d’un compte GitHub et installer Git pour Windows sur votre système. Consultez la page [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Inscription à un nouveau compte GitHub) et [Git for Windows](https://git-for-windows.github.io/) (Git pour Windows) pour plus d’informations.  

1. Accédez au dépôt que vous souhaitez cloner sur GitHub.  

1. Cliquez sur le bouton **Cloner ou télécharger**, puis choisissez le bouton **Copier dans le Presse-papiers** du menu déroulant pour copier l’URL sécurisée pour le dépôt GitHub.  

  ![Bouton de clonage GitHub](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  Tandis que vous avez également la possibilité d’ouvrir le projet sur votre bureau ou de télécharger un fichier .zip du projet, cet exemple montre comment cloner le référentiel à l’aide de la méthode de l’URL sécurisée.

1. Dans Visual Studio, cliquez sur l’onglet **Team Explorer** onglet pour ouvrir Team Explorer.  

1. Dans Team Explorer, sous la section relative aux **référentiels Git locaux** , choisissez la commande **Cloner**, puis collez l’URL de la page GitHub dans la zone de texte.  

  ![Cloner le projet](./media/VSIDE_Code_Clone2.png)

1. Cliquez sur le bouton **Cloner** pour cloner les fichiers du projet dans un référentiel Git local. Ceci peut prendre plusieurs minutes, selon la taille du référentiel.  

1. Une fois le dépôt cloné sur votre système, dans Team Explorer, choisissez la commande **Ouvrir** dans le menu contextuel (clic droit) du dépôt qui vient d’être cloné.  

  ![Dépôt cloné](./media/VSIDE_Code_Clone3.png)

1. Choisissez la commande **Présenter l’affichage des dossiers** pour afficher les fichiers dans l’Explorateur de solutions  

  ![Présenter l’affichage des dossiers](./media/VSIDE_Code_Clone3_show.png)

  Vous pouvez parcourir les dossiers et fichiers dans le dépôt cloné, et afficher et rechercher le code dans l’éditeur de code Visual Studio, avec la colorisation de la syntaxe et d’autres fonctionnalités.

    ![Recherche de code de projet cloné](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")  |    [Regarder une vidéo](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) montrant comment cloner et ouvrir du code à partir d’un dépôt GitHub dans Visual Studio. |

## <a name="debug-your-code"></a>Déboguer votre code

Vous pouvez déboguer votre code dans Visual Studio sans projet ou solution. Pour déboguer certains langages, vous devrez peut-être spécifier un *fichier de démarrage* valide dans le projet de code, tel qu’un script, un exécutable ou un projet. Visual Studio exécute tout d’abord le code spécifié lorsque vous déboguez votre code.  

La zone de liste déroulante en regard du bouton Démarrer de la barre d’outils répertorie tous les éléments de démarrage détectés par Visual Studio, ainsi que les éléments que vous choisissez spécifiquement dans un dossier.  

![Bouton Exécuter](./media/VSIDE_Code_Run_Button.png)  

Visual Studio reconnaît automatiquement les projets, toutefois les scripts (tels que Python et JavaScript) doivent être explicitement sélectionnés par vous-même comme élément de démarrage avant qu’ils ne s’affichent dans la liste. En outre, plusieurs configurations de build de certains éléments de démarrage, tels que MSBuild et CMake, peuvent s’afficher dans la liste déroulante du bouton Exécuter.  

Visual Studio prend actuellement en charge le débogage des langages suivants :  

- Node.js  

- Python  

- Projets MSBuild (C#, VB, C++)  

- N’importe quel fichier exécutable doté de fichiers PDB (outil de débogage Python).  

### <a name="to-debug-nodejs-and-python"></a>Pour déboguer Node.js et Python :

1. Installez Node.js ou Python Tools ou Visual Studio 2017 et le runtime Node.js.  

1. Dans le menu contextuel d’un fichier JavaScript de l’Explorateur de solutions, choisissez la commande **Définir comme élément de démarrage**.  

1. Appuyez sur la touche **F5** pour commencer le débogage.  

### <a name="to-debug-msbuild-projects"></a>Pour déboguer des projets MSBuild

1. Dans le menu Visual Studio, choisissez **Déboguer**. Dans le menu déroulant, sélectionnez le projet ou le fichier que vous souhaitez afficher comme élément de démarrage dans l’Explorateur de solutions.  

1. Appuyez sur la touche **F5** pour commencer le débogage.  

### <a name="to-debug-executable-files"></a>Pour déboguer des fichiers exécutables

1. Dans le menu Visual Studio, choisissez **Déboguer**. Dans le menu déroulant, sélectionnez le projet ou le fichier que vous souhaitez afficher comme élément de démarrage dans l’Explorateur de solutions.  

1. Appuyez sur la touche **F5** pour commencer le débogage.  

## <a name="enable-custom-build-tools"></a>Activer les outils de génération personnalisée

Visual Studio sait comment exécuter de nombreux langages, mais il ne sait pas comment exécuter tous les éléments. Si Visual Studio sait comment exécuter votre langage, vous pouvez exécuter le code immédiatement. Si vous essayez d’exécuter votre code, et que Visual Studio ne sait pas comment l’exécuter, une barre d’informations vous invite à désigner un fichier de votre base de code à exécuter en tant qu’élément de démarrage.  

Cependant, si le code de base utilise des outils de génération personnalisés que Visual Studio ne reconnaît pas, vous ne serez probablement pas en mesure d’exécuter et déboguer le code dans Visual Studio tant que vous n’aurez pas effectué quelques étapes supplémentaires. Vous devez spécifier un type de fichier exécutable valide, comme un compilateur, ainsi que tous les paramètres et les arguments personnalisés exigés par le langage. Pour ce faire, Visual Studio propose des *tâches de génération*. Vous pouvez créer une tâche de génération pour spécifier tous les éléments, dont un langage a besoin pour générer et exécuter son code.  

Vous pouvez également créer des tâches de génération arbitraires qui peuvent faire pratiquement tout ce que vous souhaitez. Par exemple, vous pouvez créer une tâche visant à répertorier le contenu d’un dossier ou à renommer un fichier. Ou bien, vous pouvez créer des tâches de génération personnalisée ciblées qui effectuent des opérations de compilation et de génération de votre projet à l’aide d’arguments spécifiques. Les étapes suivantes montrent comment créer les deux types de tâches de génération.  

#### <a name="to-create-an-arbitrary-build-task"></a>Pour créer une tâche de génération arbitraire

1. Dans l’Explorateur de solutions, choisissez le fichier ou le dossier du projet dans lequel vous souhaitez placer la tâche et dans le menu contextuel du fichier ou du dossier (clic droit), choisissez **Configurer les tâches**.  

  ![Configurer les tâches](./media/VSIDE_Code_Config_Task.png)

  Choisissez **Configurer les tâches** pour ouvrir un fichier appelé tasks.vs.json. Ce fichier est créé s’il n’existe pas. Ce fichier contient les tâches de génération du fichier ou dossier sélectionné.  

  ![Fichier Tasks.vs.json](./media/VSIDE_Code_Tasks_JSON.png)

1. Ajouter la tâche de génération suivante à tasks.vs.json. Pour cet exemple, nous allons ajouter une tâche simple appelée « Répertorier les sorties » qui répertorie les fichiers et sous-dossiers du dossier sélectionné dans la fenêtre Sortie. La nouvelle tâche doit être ajoutée dans le tableau « tâches » existant.  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  La tâche de génération complète doit ressembler à ceci.  

  ![Tâche de génération arbitraire](./media/VSIDE_Code_Tasks_ArbTask.png)

1. Enregistrez le projet.  

1. Ouvrez le menu contextuel du dossier sélectionné. La nouvelle tâche de génération arbitraire doit figurer au bas du menu contextuel.  

  ![Commande de tâche de génération arbitraire](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. Choisissez la nouvelle commande **Répertorier les sorties**pour exécuter la tâche.  

### <a name="to-create-a-custom-build-task"></a>Pour créer une tâche de génération personnalisée

Dans cette procédure, nous allons ajouter deux tâches de génération personnalisée utilisant nMake pour générer et nettoyer votre code.  

1. Dans l’Explorateur de solutions, choisissez un fichier du projet que vous souhaitez désigner ultérieurement comme élément de démarrage. Dans le menu contextuel (clic droit) du fichier, choisissez **Configurer les tâches**.  

  ![Commande de tâche de génération personnalisée](./media/VSIDE_Code_Tasks_CustTask1.png)

1. Ajoutez les tâches de génération suivantes à tasks.vs.json. Pour cet exemple, nous allons ajouter deux tâches : une appelée « makefile-build » qui utilise la commande nMake pour générer le projet et une autre appelée makefile-clean qui appelle la commande nMake avec l’argument « propre ». Ces tâches doivent être ajoutées au tableau « tâches » existant. Notez qu’il s’agit uniquement d’exemples de tâches de génération. Pour qu’elles fonctionnent réellement, vous devez disposer de la charge de travail qui contient [nNake](/cpp/build/nmake-reference) installé sur votre système.)

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  La tâche de génération personnalisée vcomplète doit ressembler à ceci.  

  ![Outil de génération personnalisée](./media/VSIDE_Code_Tasks_CustTask2.png)

1. Enregistrez le projet.  

1. Ouvrez le menu contextuel du fichier sélectionné. Les nouvelles tâches de génération personnalisées doivent apparaître au milieu du menu contextuel.  

  ![Commande de tâche de génération personnalisée](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > Les commandes apparaissent sous la commande **Configurer les tâches** en raison de leurs paramètres `contextType` ; « générer » et « nettoyer » sont des commandes de génération, de sorte qu’elles apparaissent dans la section génération au milieu du menu contextuel.  

  Maintenant que vous avez associé des commandes de génération personnalisée au fichier, vous pouvez désigner le fichier comme élément de démarrage.  

1. Dans le menu contextuel du fichier, choisissez **Définir comme élément de démarrage**.  

  ![Commande de tâche de génération personnalisée](./media/VSIDE_Code_Tasks_CustTask4.png)

1. Dans la barre d’outils, choisissez la flèche déroulante en regard du bouton Démarrer. L’élément de démarrage apparaît maintenant sous forme d’option.  

  ![Commande de tâche de génération personnalisée](./media/VSIDE_Code_Tasks_CustTask5.png)

Vous pouvez maintenant cliquer sur le bouton **Démarrer** ou appuyer sur la touche **F5** pour exécuter le code base. Vous pouvez modifier et déboguer votre code de base dans Visual Studio même si Visual Studio ne reconnaît pas les outils de génération du code base. La sortie de la tâche de génération s’affiche dans la fenêtre **Sortie** et les erreurs de génération apparaissent dans la **liste d’erreurs**. Le fichier de la tâche de génération tasks.vs.json associe la boucle de développement interne de Visual Studio aux outils de génération personnalisée utilisés par le code de base.  

Les tâches de génération personnalisée peuvent être ajoutées à chaque fichier ou à l’ensemble des fichiers d’un type spécifique. Par exemple, les fichiers du package NuGet peuvent être configurés de manière à obtenir une tâche « Restaurer les packages », ou tous les fichiers sources peuvent être configurés afin d’obtenir une tâche d’analyse statique, par exemple un linter pour tous les fichiers .js.  

Visual Studio prend en charge le remplacement de la variable de `$variable` VSCode à la racine de tasks.vs.json, en plus des variables d’environnement (telles que `$env.var`) ou des clés.  

## <a name="specify-build-output"></a>Spécifier la sortie de la génération

Si votre projet doit être compilé, vous pouvez ajouter une balise supplémentaire appelée `output` dans le fichier tasks.vs.json. Voici un exemple :  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

La spécification de l’emplacement de sortie indique à Visual Studio où trouver la sortie de la génération du projet.  

## <a name="tasksvsjson-file-location"></a>Emplacement du fichier tasks.vs.json

Par défaut, le fichier tasks.vs.json se trouve dans un dossier masqué appelé `.vs`. Pour afficher les fichiers masqués dans Visual Studio, cliquez sur le bouton **Afficher tous les fichiers** de la barre d’outils de l’Explorateur de solutions.

![Commande de tâche de génération arbitraire](./media/VSIDE_Code_Tasks_FileLocation.png)

Le fichier tasks.vs.json est masqué car la plupart des utilisateurs ne souhaitent généralement pas le vérifier dans le contrôle de code source. Toutefois, si vous souhaitez être en mesure de le vérifier dans le contrôle de code source, faites glisser le fichier à la racine de votre projet où il sera visible.  

D’autres fichiers .json peuvent être présents dans le dossier .vs, toutefois les fichiers tasks.vs.json et launch.vs.json (s’ils y figurent) sont les seuls à déplacer. Le fichier launch.vs.json configure l’outil de débogage de Visual Studio, tandis que le fichier tasks.vs.json configure la génération dans Visual Studio.  

## <a name="see-also"></a>Voir aussi

[Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md)
