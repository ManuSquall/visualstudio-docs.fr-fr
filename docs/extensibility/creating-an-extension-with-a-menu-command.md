---
title: Création d’une Extension avec une commande de Menu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108152"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Création d’une Extension avec une commande de Menu
Cette procédure pas à pas montre comment créer une extension avec une commande de menu qui lance le bloc-notes.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Création d’une commande de Menu  
  
1.  Créez un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Lorsque le projet s’ouvre, ajouter un modèle d’élément de commande personnalisée nommé **FirstCommand**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de commande pour **FirstCommand.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, ouvrez le **outils / Extensions et mises à jour** fenêtre. Vous devez voir le **FirstMenuCommand** extension ici. (Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstMenuCommand**).  
  
     Passez maintenant à la **outils** menu dans l’instance expérimentale. Vous devez voir **FirstCommand d’appeler** commande. À ce stade simplement afficher une boîte de message indiquant que « FirstCommandPackage à l’intérieur de FirstMenuCommand.FirstCommand.MenuItemCallback() ». Nous verrons comment démarre le bloc-notes à partir de cette commande dans la section suivante.  
  
## <a name="changing-the-menu-command-handler"></a>Modifier le Gestionnaire de commandes de Menu  
 Maintenant nous allons mettre à jour le Gestionnaire de commandes pour démarrer le bloc-notes.  
  
1.  Arrêter le débogage et revenir à votre instance de travail de Visual Studio. Ouvrez le fichier FirstCommand.cs et ajoutez le code suivant à l’aide d’instruction :  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Recherchez le constructeur FirstCommand privé. Il s’agit sur lequel la commande est raccordée au service de commande et le Gestionnaire de commandes est spécifié. Modifiez le nom du Gestionnaire de commandes à StartNotepad, comme suit :  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Supprimez la méthode MenuItemCallback et ajoutez une méthode StartNotepad qui commence juste le bloc-notes :  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Essayez maintenant. Lorsque vous commencez à déboguer le projet et cliquez sur **outils / appeler FirstCommand**, vous devez voir une instance de bloc-notes rien.  
  
     Vous pouvez utiliser une instance de la <xref:System.Diagnostics.Process> classe pour exécuter n’importe quel fichier exécutable, pas seulement le bloc-notes. Essayez avec calc.exe, par exemple.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Nettoyage de l’environnement expérimentale  
 Si vous développez plusieurs extensions, ou simplement Explorer les résultats avec différentes versions de votre code d’extension, votre environnement expérimentale peut cesser de fonctionner elle devrait. Dans ce cas, vous devez exécuter le script de réinitialisation. Il est appelé **réinitialiser l’Instance expérimentale de Visual Studio 2015**, et il est fourni avec le Kit de développement logiciel Visual Studio. Ce script supprime toutes les références à vos extensions de l’environnement expérimentale, pour que vous pouvez commencer à partir de zéro.  
  
 Vous pouvez accéder à ce script de deux manières :  
  
1.  À partir du bureau, recherchez **réinitialiser l’Instance expérimentale de Visual Studio 2015**.  
  
2.  À partir de la ligne de commande, exécutez la commande suivante :  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Déploiement de votre extension.  
 Maintenant que vous avez votre extension de l’outil en cours d’exécution comme vous le souhaitez, il est temps de réfléchir à partager avec vos amis et collègues. C’est facile, tant qu’ils disposent de Visual Studio 2015 est installé. Il vous est leur envoyer le fichier .vsix que vous avez créé. (Veillez à générer dans le mode Release.)  
  
 Vous trouverez le fichier .vsix pour cette extension dans le répertoire bin de FirstMenuCommand. Plus précisément, en supposant que vous avez créé la configuration Release, il sera dans :  
  
 **\<répertoire de code > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Pour installer l’extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double-cliquez sur le fichier .vsix, qui affiche le **programme d’installation de VSIX**. Les fichiers sont copiés dans le **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** active.  
  
 Lorsque votre ami met à jour Visual Studio à nouveau, il trouverez l’extension FirstMenuCommand dans **outils / Extensions et mises à jour**. Il peut atteindre **Extensions et mises à jour** pour désinstaller ou désactiver l’extension, trop.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas vous a montré qu’une petite partie de ce que vous pouvez faire avec une extension de Visual Studio. Voici une liste courte d’autres choses (relativement faciles), que vous pouvez faire avec les extensions Visual Studio :  
  
1.  Vous pouvez effectuer bien d’autres choses avec une commande de menu simple :  
  
    1.  Ajouter votre propre icône : [Ajout d’icônes aux commandes de Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modifier le texte de la commande de menu : [modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Ajouter un raccourci de menu à une commande : [liaison des raccourcis clavier aux éléments de Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Ajouter différents types de commandes, menus et barres d’outils : [extension des Menus et des commandes](../extensibility/extending-menus-and-commands.md)  
  
3.  Ajouter des fenêtres Outil et d’étendre des fenêtres Outil Visual Studio intégrés : [extension et la personnalisation des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Ajout d’IntelliSense, des suggestions de code, et d’autres fonctionnalités dans les éditeurs de code : [étendre l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Ajouter des pages de propriété et les Options et paramètres utilisateur pour votre extension : [étendre les propriétés et la fenêtre des propriétés](../extensibility/extending-properties-and-the-property-window.md) et [Options et paramètres utilisateur d’extension](../extensibility/extending-user-settings-and-options.md)  
  
 D’autres types d’extensions nécessitent un peu plus de travail, telles que la création d’un nouveau type de projet ([extension des projets](../extensibility/extending-projects.md)), création d’un nouveau type d’éditeur ([créer des éditeurs personnalisés et les concepteurs](../extensibility/creating-custom-editors-and-designers.md)), ou implémentation de votre extension dans un shell isolé : [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)