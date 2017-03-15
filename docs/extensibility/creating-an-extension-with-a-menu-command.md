---
title: "Cr&#233;ation d&#39;une Extension avec une commande de Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "écrire un vspackage"
  - "VSPackage"
  - "didacticiels"
  - "package Visual studio"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 56
---
# Cr&#233;ation d&#39;une Extension avec une commande de Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une extension avec une commande de menu qui lance le bloc\-notes.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'une commande de Menu  
  
1.  Créez un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Lorsque le projet s'ouvre, ajoutez un modèle d'élément commande personnalisée nommé **FirstCommand**. Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **FirstCommand.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L'instance expérimentale de Visual Studio s'affiche. Pour plus d'informations sur l'instance expérimentale, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l'instance expérimentale, ouvrez le  **Outils \/ Extensions et mises à jour** fenêtre. Vous devez voir les **FirstMenuCommand** extension ici. \(Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstMenuCommand**\).  
  
     Passez maintenant à la **outils** menu dans l'instance expérimentale. Vous devez voir **FirstCommand appeler** commande. À ce stade simplement afficher une boîte de message indiquant que « FirstCommandPackage dans FirstMenuCommand.FirstCommand.MenuItemCallback\(\) ». Nous verrons comment faire pour démarrer le bloc\-notes à partir de cette commande dans la section suivante.  
  
## Modification du Gestionnaire de commandes de Menu  
 Maintenant nous allons mettre à jour le Gestionnaire de commandes pour démarrer le bloc\-notes.  
  
1.  Arrêter le débogage et revenir à votre instance de travail de Visual Studio. Ouvrez le fichier FirstCommand.cs et ajoutez l'instruction using :  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  Recherchez le constructeur FirstCommand privé. C'est la commande est raccordée au service de commande et le Gestionnaire de commandes est spécifié. Remplacez le nom du Gestionnaire de commandes StartNotepad, comme suit :  
  
    ```c#  
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
  
3.  Supprimez la méthode MenuItemCallback et ajouter une méthode StartNotepad qui démarrera simplement le bloc\-notes :  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Essayez maintenant. Lorsque vous commencez à déboguer le projet et cliquez sur **Outils \/ appeler FirstCommand**, vous devez voir une instance du bloc\-notes à trouver.  
  
     Vous pouvez utiliser une instance de la <xref:System.Diagnostics.Process> classe doit s'exécuter n'importe quel fichier exécutable, pas seulement le bloc\-notes. Essayez avec calc.exe, par exemple.  
  
## Nettoyage de l'environnement expérimental  
 Si vous développez plusieurs extensions, ou simplement Explorer les résultats avec différentes versions de votre code d'extension, votre environnement expérimental peut cesser de fonctionner correctement. Dans ce cas, vous devez exécuter le script de réinitialisation. Il est appelé **Réinitialiser l'Instance expérimentale de Visual Studio 2015**, et il est fourni avec le Kit de développement Visual Studio. Ce script supprime toutes les références à vos extensions de l'environnement expérimental, vous pouvez donc commencer à partir de zéro.  
  
 Vous pouvez accéder à ce script de deux manières :  
  
1.  À partir du bureau, recherchez **Réinitialiser l'Instance expérimentale de Visual Studio 2015**.  
  
2.  À partir de la ligne de commande, exécutez la commande suivante :  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## Déploiement de votre extension  
 Maintenant que vous avez votre extension de l'outil en cours d'exécution comme vous le souhaitez, il est temps de réfléchir à partager avec vos amis et collègues. C'est facile, tant qu'ils disposent de Visual Studio 2015 est installé. Il vous suffit est leur envoyer le fichier .vsix que vous avez créé. \(Veillez à générer en mode version finale\).  
  
 Vous trouverez le fichier .vsix pour cette extension dans le répertoire bin de FirstMenuCommand. En particulier, en supposant que vous avez créé la configuration Release, il se présente :  
  
 **\< répertoire code \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 Pour installer l'extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double\-cliquez sur le fichier .vsix, qui permet d'afficher le **installateur VSIX**. Les fichiers sont copiés dans le **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** active.  
  
 Lorsque votre ami met à jour de Visual Studio à nouveau, il y trouverez l'extension FirstMenuCommand dans **Outils \/ Extensions et mises à jour**. Il peut atteindre **Extensions et mises à jour** pour désinstaller ou désactiver l'extension, trop.  
  
## Étapes suivantes  
 Cette procédure pas à pas vous a montré qu'une petite partie de ce que vous pouvez faire avec une extension Visual Studio. Voici une courte liste d'autres choses \(raisonnablement faciles\), que vous pouvez faire avec les extensions Visual Studio :  
  
1.  Vous pouvez faire tellement plus avec une commande de menu simple :  
  
    1.  Ajoutez votre propre icône : [Ajouter des icônes aux commandes de Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modifier le texte de la commande : [Modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Ajouter un raccourci de menu à une commande : [Raccourcis clavier de liaison aux éléments de Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Ajouter différents types de commandes, des menus et barres d'outils : [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)  
  
3.  Ajouter des fenêtres Outil et d'étendre les fenêtres d'outil Visual Studio intégrés : [Extension et personnalisation des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Ajoutez des suggestions de code, IntelliSense et d'autres fonctionnalités pour les éditeurs de code existant : [Extension de l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Ajouter des paramètres utilisateur et les pages d'Options et de la propriété à votre extension : [Étendre les propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md) et [Options et paramètres d'extension utilisateur](../extensibility/extending-user-settings-and-options.md)  
  
 D'autres types d'extensions nécessitent un peu plus de travail, telles que la création d'un nouveau type de projet \([Étendre des projets](../extensibility/extending-projects.md)\), la création d'un nouveau type d'éditeur \([Création de concepteurs et éditeurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)\), ou l'implémentation de votre extension dans un environnement isolé : [Isolé du Shell Visual Studio](../extensibility/visual-studio-isolated-shell.md)