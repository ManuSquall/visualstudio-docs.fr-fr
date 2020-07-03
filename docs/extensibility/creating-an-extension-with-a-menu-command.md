---
title: Création d’une extension à l’aide d’une commande de menu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f9e9963e05b0991beaea7da4027f4db3df4e4eb
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903921"
---
# <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu

Cette procédure pas à pas montre comment créer une extension avec une commande de menu qui lance le bloc-notes.

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Créer une commande de menu

1. Créez un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **FirstCommand**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >  **Extensibility** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *FirstCommand.cs*.

3. Générez le projet et commencez le débogage.

    L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Dans l’instance expérimentale, ouvrez la **Tools**  >  fenêtre**extensions et mises à jour** des outils. Vous devez voir l’extension **FirstMenuCommand** ici. (Si vous ouvrez **extensions et mises à jour** dans votre instance de Visual Studio qui fonctionne, vous ne voyez pas **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. Dans l’instance expérimentale, ouvrez la fenêtre **Extensions**de  >  **gestion** des extensions. Vous devez voir l’extension **FirstMenuCommand** ici. (Si vous ouvrez **gérer les extensions** dans votre instance de Visual Studio, vous ne voyez pas **FirstMenuCommand**).

::: moniker-end

Maintenant, accédez au menu **Outils** de l’instance expérimentale. La commande **Invoke FirstCommand** doit s’afficher. À ce stade, la commande affiche une boîte de message indiquant **FirstCommandPackage dans FirstMenuCommand. FirstCommand. MenuItemCallback ()**. Nous verrons comment démarrer le bloc-notes à partir de cette commande dans la section suivante.

## <a name="change-the-menu-command-handler"></a>Modifier le gestionnaire de commandes de menu

À présent, nous allons mettre à jour le gestionnaire de commandes pour démarrer le bloc-notes.

1. Arrêtez le débogage et revenez à votre instance de travail de Visual Studio. Ouvrez le fichier *FirstCommand.cs* et ajoutez l’instruction using suivante :

    ```csharp
    using System.Diagnostics;
    ```

2. Recherchez le constructeur Private FirstCommand. C’est là que la commande est raccordée au service de commande et que le gestionnaire de commandes est spécifié. Remplacez le nom du gestionnaire de commandes par StartNotepad, comme suit :

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Supprimez la `MenuItemCallback` méthode et ajoutez une `StartNotepad` méthode, qui démarre simplement le bloc-notes :

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Essayez maintenant. Quand vous démarrez le débogage du projet et que vous cliquez sur **Outils**  >  **appeler FirstCommand**, une instance du bloc-notes doit apparaître.

    Vous pouvez utiliser une instance de la <xref:System.Diagnostics.Process> classe pour exécuter n’importe quel exécutable, pas seulement le bloc-notes. Essayez-le avec `calc.exe` , par exemple.

## <a name="clean-up-the-experimental-environment"></a>Nettoyer l’environnement expérimental

Si vous développez plusieurs extensions ou explorez uniquement les résultats avec des versions différentes de votre code d’extension, votre environnement expérimental peut cesser de fonctionner comme il le devrait. Dans ce cas, vous devez exécuter le script de réinitialisation. Elle est appelée **Réinitialiser l’instance expérimentale de Visual Studio**, et elle est fournie dans le cadre du kit de développement logiciel (SDK) Visual Studio. Ce script supprime toutes les références à vos extensions de l’environnement expérimental, de sorte que vous pouvez commencer à partir de zéro.

Vous pouvez accéder à ce script de deux manières :

1. À partir du bureau, recherchez **Réinitialiser l’instance expérimentale de Visual Studio**.

2. À partir de la ligne de commande, exécutez ce qui suit :

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Déployer votre extension

Maintenant que votre extension d’outil fonctionne comme vous le souhaitez, il est temps de réfléchir au partage avec vos amis et collègues. C’est facile, à condition que Visual Studio 2015 soit installé. Il vous suffit de leur envoyer le fichier *. vsix* que vous avez créé. (Veillez à le générer en mode release.)

Vous pouvez trouver le fichier *. vsix* pour cette extension dans le répertoire bin *FirstMenuCommand* . En particulier, en supposant que vous ayez créé la configuration Release, elle sera dans :

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix*

Pour installer l’extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double-cliquer sur le fichier *. vsix* , qui affiche le **programme d’installation VSIX**. Les fichiers sont copiés dans le répertoire *%LocalAppData%\Microsoft\VisualStudio \<version> \Extensions*

Quand votre ami rétablit Visual Studio, il trouve l’extension FirstMenuCommand dans **Outils**  >  **extensions et mises à jour**. Ils peuvent également accéder à **extensions et mises à jour** pour désinstaller ou désactiver l’extension.

## <a name="next-steps"></a>Étapes suivantes

Cette procédure pas à pas vous a montré une petite partie de ce que vous pouvez faire avec une extension Visual Studio. Voici une brève liste d’autres choses (raisonnablement faciles) que vous pouvez faire avec les extensions Visual Studio :

1. Vous pouvez faire beaucoup d’autres choses avec une simple commande de menu :

   1. Ajouter votre propre icône : [Ajouter des icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Modifier le texte de la commande de menu : [modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Ajouter un raccourci de menu à une commande : [lier des raccourcis clavier à des éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Ajoutez différents types de commandes, de menus et de barres d’outils : [étendre des menus et des commandes](../extensibility/extending-menus-and-commands.md)

3. Ajoutez des fenêtres outil et étendez les fenêtres Outil Visual Studio intégrées : [étendre et personnaliser les fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md)

4. Ajouter IntelliSense, des suggestions de code et d’autres fonctionnalités aux éditeurs de code existants : [étendre l’éditeur et les services de langage](../extensibility/extending-the-editor-and-language-services.md)

5. Ajoutez des options et des pages de propriétés et des paramètres utilisateur à votre extension : [étendre les propriétés et la fenêtre de propriétés](../extensibility/extending-properties-and-the-property-window.md) et [étendre les paramètres utilisateur et les options](../extensibility/extending-user-settings-and-options.md)

   D’autres types d’extensions nécessitent un peu plus de travail, telles que la création d’un nouveau type de projet ([étendre des projets](../extensibility/extending-projects.md)), la création d’un nouveau type d’éditeur ([création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)) ou l’implémentation de votre extension dans un interpréteur de commandes isolé : [Visual Studio isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
