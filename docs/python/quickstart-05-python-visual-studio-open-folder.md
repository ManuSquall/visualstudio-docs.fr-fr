---
title: Démarrage rapide - Ouvrir un dossier de code Python
description: Dans ce démarrage rapide, vous ouvrez et exécutez du code Python à partir d’un dossier sans utiliser de projet Visual Studio (Visual Studio 2019 uniquement).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: a7bf174191a6a2fb013aa3d25880b01bc2e7f070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801670"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Démarrage rapide : ouvrir et exécuter du code python dans un dossier

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2019](installing-python-support-in-visual-studio.md), il est facile d’exécuter du code Python existant dans Visual Studio 2019 sans créer de projet Visual Studio.

> [!Note]
> Visual Studio 2017 et antérieur vous oblige à créer un projet Visual Studio pour exécuter du code Python, ce que vous pouvez faire facilement avec un modèle de projet intégré. Consultez [démarrage rapide : créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Pour cette procédure pas à pas, vous pouvez utiliser n’importe quel dossier avec le code Python que vous souhaitez. Pour suivre l’exemple présenté ici, clonez le référentiel GitHub gregmalcolm/python_koans sur votre ordinateur à l’aide de la commande `git clone https://github.com/gregmalcolm/python_koans` dans un dossier approprié.

1. Lancez Visual Studio 2019 puis, dans la fenêtre de démarrage, sélectionnez **Ouvrir** en bas de la colonne **Prise en main**. Sinon, si vous avez déjà installé Visual Studio, sélectionnez plutôt la commande **fichier**  >  **ouvrir**le  >  **dossier** .

    ![L’écran de démarrage de Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Accédez au dossier contenant votre code Python, puis choisissez **Sélectionner un dossier**. Si vous utilisez le code python_koans, veillez à sélectionner le dossier `python3` dans le dossier clone.

    ![La boîte de dialogue Sélectionner un dossier à partir de la commande Ouvrir un dossier](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio affiche le dossier dans l’**Explorateur de solutions** dans ce que l’on appelle **Affichage des dossiers**. Vous pouvez développer et réduire les dossiers à l’aide de flèches situées sur les bords gauche des noms de dossiers :

    ![Contrôles pour développer et réduire les dossiers dans l’Explorateur de solutions](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Lorsque vous ouvrez un dossier Python, Visual Studio crée plusieurs dossiers cachés pour gérer les paramètres liés au projet. Pour afficher ces dossiers (et les autres fichiers et dossiers cachés, tels que le dossier *.git*), sélectionnez le bouton de barre d’outils **Afficher tous les fichiers** :

    ![Un affichage des dossiers cachés dans l’Explorateur de solutions](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Pour exécuter le code, vous devez tout d’abord identifier le fichier de démarrage ou de programme principal. Dans l’exemple présenté ici, le fichier de démarrage est *contemplate-koans.py*. Cliquez avec le bouton droit sur ce fichier et sélectionnez **Définir comme élément de démarrage**.

    ![Définition d’un élément de démarrage dans l’Explorateur de solutions](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Si votre élément de démarrage ne se trouve pas à la racine du dossier que vous avez ouvert, vous devez également ajouter une ligne au fichier JSON de configuration de démarrage comme décrit dans la section [Définir un répertoire de travail](#set-a-working-directory).

1. Exécutez le code en appuyant sur **CTRL** + **F5** ou en sélectionnant **Déboguer**  >  **exécuter sans débogage**. Vous pouvez également sélectionner le bouton de barre d’outils qui affiche l’élément de démarrage avec un bouton de lecture, qui exécute du code dans le débogueur Visual Studio. Dans tous les cas, Visual Studio détecte que votre élément de démarrage est un fichier Python, il exécute ainsi automatiquement le code dans l’environnement Python par défaut. (Cet environnement est indiqué à droite de l’élément de démarrage sur la barre d’outils.)

    ![Bouton de barre d’outils de démarrage du débogueur](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. La sortie du programme s’affiche dans une fenêtre de commande distincte :

    ![Fenêtre de sortie d’exécution de code Python](media/quickstart-open-folder/08-result-window.png)

1. Pour exécuter le code dans un autre environnement, sélectionnez ce dernier dans le contrôle de liste déroulante de la barre d’outils, puis relancez l’élément de démarrage.

1. Pour fermer le dossier dans Visual Studio, sélectionnez la commande de menu **fichier**  >  **Fermer le dossier** .

## <a name="set-a-working-directory"></a>Définir un répertoire de travail

Par défaut, Visual Studio exécute un projet Python ouvert en tant que dossier à la racine de ce même dossier. Le code dans votre projet peut toutefois supposer que Python est en cours d’exécution dans un sous-dossier. Par exemple, supposons que vous ouvrez le dossier racine du référentiel python_koans et que vous définissez le fichier *python3/contemplate-koans.py* comme élément de démarrage. Si vous exécutez ensuite le code, vous voyez une erreur telle que le fichier *koans.txt* est introuvable. Cette erreur se produit car *contemplate-koans.py* part du principe que Python est en cours d’exécution dans le dossier *python3* plutôt qu’à la racine du référentiel.

Dans ce cas, vous devez également ajouter une ligne au fichier JSON de configuration de démarrage pour spécifier le répertoire de travail :

1. Cliquez avec le bouton droit sur le fichier de démarrage Python (*.py*) dans l’**Explorateur de solutions** et sélectionnez **Paramètres de débogage et de lancement**.

    ![La commande Paramètres de débogage et de lancement pour un fichier Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Dans la boîte de dialogue **Sélectionner un débogueur** qui s’affiche, sélectionnez **Par défaut**, puis choisissez **Sélectionner**.

    ![La commande Paramètres de débogage et de lancement pour un fichier Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Si vous ne voyez pas la **valeur par défaut** , assurez-vous de choisir un fichier python *. py* lors de la sélection de la commande **Déboguer et lancer les paramètres** . Visual Studio utilise le type de fichier pour déterminer les options de débogueur à afficher.

1. Visual Studio ouvre un fichier nommé *launch.vs.json*, qui se trouve dans le dossier *.vs* caché. Ce fichier décrit le contexte de débogage du projet. Pour spécifier un répertoire de travail, ajoutez une valeur pour `"workingDirectory"`, comme dans `"workingDirectory": "python3"` pour l’exemple python-koans :

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Enregistrez le fichier et relancez le programme qui s’exécute maintenant dans le dossier spécifié.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Tutoriel : Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : créer un projet Python à partir de code existant](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Démarrage rapide : créer un projet Python à partir d’un référentiel](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
