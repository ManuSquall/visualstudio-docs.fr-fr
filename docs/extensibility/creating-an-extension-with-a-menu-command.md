---
title: Création d’une extension avec une commande de menu Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739560"
---
# <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu

Ce pas-là montre comment créer une extension avec une commande de menu qui lance Notepad.

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Créer une commande de menu

1. Créer un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **FirstCommand**. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *FirstCommand.cs*.

3. Générez le projet et commencez le débogage.

    L’exemple expérimental de Visual Studio apparaît. Pour plus d’informations sur l’instance expérimentale, voir [L’exemple expérimental](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Dans le cas expérimental, ouvrez la fenêtre **Tools** > **Extensions and Updates.** Vous devriez voir l’extension **FirstMenuCommand** ici. (Si vous ouvrez **extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. Dans le cas expérimental, ouvrez la fenêtre **Extensions** > **Manage Extensions.** Vous devriez voir l’extension **FirstMenuCommand** ici. (Si vous ouvrez **Manage Extensions** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstMenuCommand**).

::: moniker-end

Maintenant, allez au menu **Tools** dans l’exemple expérimental. Vous devriez voir **Invoke FirstCommand** commande. À ce stade, la commande apporte une boîte de message qui dit **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Nous allons voir comment réellement démarrer Notepad à partir de cette commande dans la section suivante.

## <a name="change-the-menu-command-handler"></a>Modifier le gestionnaire de commande du menu

Maintenant, nous allons mettre à jour le gestionnaire de commande pour démarrer Notepad.

1. Arrêtez de débogage et retournez à votre instance de travail de Visual Studio. Ouvrez le fichier *FirstCommand.cs* et ajoutez l’instruction suivante à l’aide de :

    ```csharp
    using System.Diagnostics;
    ```

2. Trouvez le constructeur privé FirstCommand. C’est là que la commande est raccordée au service de commande et le gestionnaire de commande est spécifié. Changez le nom du gestionnaire de commande pour StartNotepad, comme suit :

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

3. Supprimer `MenuItemCallback` la méthode `StartNotepad` et ajouter une méthode, qui va juste démarrer Notepad:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Maintenant, essayez-le. Lorsque vous commencez à débogage du projet et cliquez sur **Outils** > **Invoquer FirstCommand**, vous devriez voir une instance de Notepad venir.

    Vous pouvez utiliser une <xref:System.Diagnostics.Process> instance de la classe pour exécuter n’importe quel runable, pas seulement Notepad. Essayez-le `calc.exe`avec , par exemple.

## <a name="clean-up-the-experimental-environment"></a>Nettoyer l’environnement expérimental

Si vous développez plusieurs extensions, ou tout simplement explorer les résultats avec différentes versions de votre code d’extension, votre environnement expérimental peut cesser de fonctionner comme il se doit. Dans ce cas, vous devez exécuter le script de réinitialisation. Il s’appelle **Reset the Visual Studio Experimental Instance**, et il expédie dans le cadre du Studio visuel SDK. Ce script supprime toutes les références à vos extensions de l’environnement expérimental, de sorte que vous pouvez commencer à partir de zéro.

Vous pouvez obtenir ce script de deux façons:

1. Depuis le bureau, trouvez **Reset the Visual Studio Experimental Instance**.

2. À partir de la ligne de commande, exécutez ce qui suit :

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Déployez votre extension

Maintenant que vous avez votre extension d’outil en cours d’exécution de la façon dont vous voulez, il est temps de penser à le partager avec vos amis et collègues. C’est facile, tant qu’ils ont Visual Studio 2015 installé. Tout ce que vous avez à faire est de leur envoyer le fichier *.vsix* que vous avez construit. (Assurez-vous de le construire en mode Libération.)

Vous pouvez trouver le fichier *.vsix* pour cette extension dans le *répertoire firstMenuCommand* bin. Plus précisément, en supposant que vous avez construit la configuration De version, il sera dans:

*\<répertoire de code>-FirstMenuCommand-FirstMenuCommand-bin-ReleaseMD FirstMenuCommand.vsix*

Pour installer l’extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double-cliquez sur le fichier *.vsix,* qui soulève **l’installateur VSIX**. Les fichiers sont copiés à la *version %LocalAppData%-Microsoft-VisualStudio\<>-Extensions* répertoire.

Lorsque votre ami évoque Visual Studio à nouveau, ils trouveront l’extension FirstMenuCommand dans **Tools** > **Extensions and Updates**. Ils peuvent aller à **Extensions et Mises** à jour pour désinstaller ou désactiver l’extension, aussi.

## <a name="next-steps"></a>Étapes suivantes

Cette procédure pas à pas vous a montré seulement une petite partie de ce que vous pouvez faire avec une extension Visual Studio. Voici une courte liste d’autres choses (raisonnablement faciles) que vous pouvez faire avec les extensions Visual Studio:

1. Vous pouvez faire beaucoup plus de choses avec une commande de menu simple:

   1. Ajoutez votre propre icône : [Ajoutez des icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Modifier le texte de la commande du menu : [Modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Ajoutez un raccourci de menu à une commande : [lier les raccourcis clavier aux éléments du menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Ajoutez différents types de commandes, de menus et de barres d’outils : [étendre les menus et les commandes](../extensibility/extending-menus-and-commands.md)

3. Ajoutez des fenêtres d’outils et étendez les fenêtres intégrées de l’outil Visual Studio : [Étendre et personnaliser les fenêtres d’outils](../extensibility/extending-and-customizing-tool-windows.md)

4. Ajoutez IntelliSense, suggestions de code et autres fonctionnalités aux éditeurs de code existants : [Étendre l’éditeur et les services linguistiques](../extensibility/extending-the-editor-and-language-services.md)

5. Ajoutez des pages Options et propriétés et paramètres de l’utilisateur à votre extension : [Étendre les propriétés et la fenêtre de propriété](../extensibility/extending-properties-and-the-property-window.md) et étendre les paramètres et options de [l’utilisateur](../extensibility/extending-user-settings-and-options.md)

   D’autres types d’extensions nécessitent un peu plus de travail, comme la création d’un nouveau type de projet ([Extend projects](../extensibility/extending-projects.md)), la création d’un nouveau type d’éditeur[(Créer des éditeurs et des concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)), ou la mise en œuvre de votre extension dans une coquille isolée: [Visual Studio coquille isolée](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
