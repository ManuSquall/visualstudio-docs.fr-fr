---
title: Développer du code sans projets ni solutions
ms.date: 06/22/2020
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75aeb721ea5625523d29e20193ac406037abedc2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284891"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Développer du code dans Visual Studio sans projets ni solutions

Vous pouvez ouvrir du code à partir de quasiment n’importe quel type de projet basé sur un répertoire dans Visual Studio sans devoir recourir à un fichier solution ou un fichier projet. Cela signifie que vous pouvez, par exemple, cloner un référentiel sur GitHub, l’ouvrir directement dans Visual Studio et commencer à développer sans avoir à créer de solution ou de projet. Si nécessaire, vous pouvez spécifier des tâches de génération et des paramètres de lancement personnalisés à l’aide de simples fichiers JSON.

Une fois que vous avez ouvert vos fichiers de code dans Visual Studio, l’**Explorateur de solutions** les affiche dans le dossier. Vous pouvez cliquer sur n’importe quel fichier pour le modifier. En arrière-plan, Visual Studio démarre l’indexation des fichiers pour activer les fonctionnalités IntelliSense, de navigation et de refactorisation. Au fil des modifications, créations, déplacements et suppressions de fichiers, Visual Studio effectue automatiquement le suivi des modifications et met à jour en permanence son index IntelliSense. Le code apparaît avec coloration syntaxique ; dans de nombreux cas, il comprend la saisie semi-automatique des instructions IntelliSense de base.

## <a name="open-any-code"></a>Ouvrir du code

Vous pouvez ouvrir du code dans Visual Studio de différentes façons :

- Dans la barre de menus de Visual Studio, choisissez **fichier**  >  **ouvrir**  >  le**dossier**, puis accédez à l’emplacement du code.

- Dans le menu contextuel (clic droit) d’un dossier contenant le code, choisissez la commande **Ouvrir dans Visual Studio**.

::: moniker range="vs-2017"
- Choisissez le lien **Ouvrir le dossier** dans la **Page de démarrage** de Visual Studio.

    > [!IMPORTANT]
    > Tout le code ne peut pas être ouvert à l’aide du lien **ouvrir le dossier** à partir de la **page de démarrage**de Visual Studio. Par exemple, si votre fichier de code a été enregistré dans le cadre d’une solution &mdash; en d’autres termes, dans un fichier. sln, &mdash; vous devez utiliser l’une des autres options répertoriées ici pour ouvrir votre code.

::: moniker-end

::: moniker range=">=vs-2019"
- Choisissez le lien **Ouvrir le dossier** dans la fenêtre de démarrage.

    > [!IMPORTANT]
    > Tout le code ne peut pas être ouvert à l’aide du lien **ouvrir le dossier** de la fenêtre de démarrage de Visual Studio. Par exemple, si votre fichier de code a été enregistré dans le cadre d’une solution &mdash; en d’autres termes, dans un fichier. sln, &mdash; vous devez utiliser l’une des autres options répertoriées ici pour ouvrir votre code.

::: moniker-end

- Si vous êtes un utilisateur du clavier, appuyez sur **CTRL** + **MAJ** + **ALT** + **O** dans Visual Studio.

- Ouvrez le code d’un référentiel GitHub cloné.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Pour ouvrir du code à partir d’un référentiel GitHub cloné

L’exemple suivant montre comment cloner un référentiel GitHub, puis ouvrir son code dans Visual Studio. Pour suivre cette procédure, vous devez disposer d’un compte GitHub et installer Git pour Windows sur votre système. Consultez la page [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Inscription à un nouveau compte GitHub) et [Git for Windows](https://git-for-windows.github.io/) (Git pour Windows) pour plus d’informations.

1. Accédez au dépôt que vous souhaitez cloner sur GitHub.

1. Cliquez sur le bouton **Cloner ou télécharger**, puis choisissez le bouton **Copier dans le Presse-papiers** du menu déroulant pour copier l’URL sécurisée pour le dépôt GitHub.

   ![Bouton de clonage GitHub](./media/VSIDE_Code_Clone.png)

1. Dans Visual Studio, choisissez l’onglet **Team Explorer** pour ouvrir **Team Explorer**. Si vous ne voyez pas l’onglet, ouvrez-le à partir de l' **affichage**  >  **Team Explorer**.

1. Dans Team Explorer, sous la section relative aux **référentiels Git locaux** , choisissez la commande **Cloner**, puis collez l’URL de la page GitHub dans la zone de texte.

   ![Cloner le projet](./media/VSIDE_Code_Clone2.png)

1. Cliquez sur le bouton **Cloner** pour cloner les fichiers du projet dans un référentiel Git local. Ceci peut prendre plusieurs minutes, selon la taille du référentiel.

1. Une fois le référentiel cloné sur votre système, dans **Team Explorer**, choisissez la commande **ouvrir** dans le menu contextuel (clic droit) du référentiel récemment cloné.

   ![Dépôt cloné](./media/VSIDE_Code_Clone3.png)

1. Choisissez la commande **Présenter l’affichage des dossiers** pour afficher les fichiers dans l’**Explorateur de solutions**.

   ![Présenter l’affichage des dossiers](./media/VSIDE_Code_Clone3_show.png)

   Vous pouvez parcourir les dossiers et fichiers dans le dépôt cloné, et afficher et rechercher le code dans l’éditeur de code Visual Studio, avec la colorisation de la syntaxe et d’autres fonctionnalités.

## <a name="run-and-debug-your-code"></a>Exécuter et déboguer son code

Vous pouvez déboguer votre code dans Visual Studio sans projet ni solution ! Dans certains langages, vous devrez peut-être spécifier un *fichier de démarrage* valide dans le codebase, par exemple, un script, un exécutable ou un projet. La zone de liste déroulante à côté du bouton **Démarrer** de la barre d’outils répertorie tous les éléments de démarrage détectés par Visual Studio, ainsi que les éléments spécifiquement désignés par vos soins. Visual Studio exécute tout d’abord ce code lors du débogage.

La façon de configurer le code pour qu’il s’exécute dans Visual Studio diffère selon le type de code et les outils de génération.

### <a name="codebases-that-use-msbuild"></a>Codebases qui utilisent MSBuild

Les codebases MSBuild peuvent avoir plusieurs configurations de build qui s’affichent dans la liste déroulante du bouton **Démarrer**. Sélectionnez le fichier que vous souhaitez utiliser comme élément de démarrage, puis cliquez sur le bouton **Démarrer** pour commencer le débogage.

> [!NOTE]
> Dans le cas des codebases C# et Visual Basic, vous devez installer la charge de travail **Développement Desktop .NET**. Dans le cas des codebases C++, vous devez installer la charge de travail **Développement Desktop en C++**.

### <a name="codebases-that-use-custom-build-tools"></a>Codebases qui utilisent des outils de génération personnalisés

Si votre codebase utilise des outils de génération personnalisés, vous devez indiquer à Visual Studio comment générer votre code à l’aide des *tâches de génération* définies dans un fichier *.json*. Pour plus d’informations, consultez la page [Personnaliser les tâches de génération et de débogage](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Codebases qui contiennent du code Python ou JavaScript

Si votre codebase contient du code Python ou JavaScript, il est inutile de configurer les fichiers *.json*, mais vous devez installer la charge de travail correspondante. Il vous faudra également configurer le script de démarrage :

1. Installez la charge de travail développement [Node.js](https://visualstudio.microsoft.com/vs/node-js/) ou de [développement python](https://visualstudio.microsoft.com/vs/python/) en choisissant **Outils**  >  **accéder aux outils et aux fonctionnalités**, ou en fermant Visual Studio et en exécutant l’Visual Studio installer.

   ![Charges de travail de développement Node.js et Python](media/python_nodejs_workloads.png)

1. Dans **l’Explorateur de solutions**, dans le menu contextuel ou le menu accessible par clic droit d’un fichier JavaScript ou Python, choisissez la commande **Définir comme élément de démarrage**.

1. Choisissez le bouton **Démarrer** pour commencer le débogage.

### <a name="codebases-that-contain-c-code"></a>Codebases qui contiennent du code C++

Pour savoir comment ouvrir du code C++ sans solutions ni projets dans Visual Studio, consultez la page [Ouvrir des projets de dossier pour C++](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Codebases qui contiennent un projet Visual Studio

Si votre dossier de code contient un projet Visual Studio, vous pouvez désigner ce projet comme élément de démarrage.

![Définir un projet comme élément de démarrage](media/customize-set-project-as-startup-item.png)

Le texte du bouton **Démarrer** évolue pour refléter le fait que le projet est l’élément de démarrage.

![Projet sur le bouton Démarrer](media/customize-start-button-project.png)

## <a name="see-also"></a>Voir aussi

- [Personnaliser des tâches de génération et de débogage](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Projets Dossier ouvert pour C++](/cpp/build/open-folder-projects-cpp)
- [Projets CMake en C++](/cpp/build/cmake-projects-in-visual-studio)
- [Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md)
