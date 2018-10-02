---
title: Création d’une Extension avec une commande de Menu | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c042dc1793add386cd91c66659ad7fd703e5580d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507938"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Création d’une extension avec une commande de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création d’une Extension avec une commande de Menu](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-a-menu-command).  
  
Cette procédure pas à pas montre comment créer une extension avec une commande de menu qui lance le bloc-notes.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Création d’une commande de Menu  
  
1.  Créez un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Quand le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisée nommé **FirstCommand**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour **FirstCommand.cs**.  
  
3.  Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4.  Dans l’instance expérimentale, ouvrez le **outils / Extensions et mises à jour** fenêtre. Vous devez voir le **FirstMenuCommand** extension ici. (Si vous ouvrez **Extensions et mises à jour** dans votre instance de travail de Visual Studio, vous ne verrez pas **FirstMenuCommand**).  
  
     Passez maintenant à la **outils** menu dans l’instance expérimentale. Vous devriez voir **FirstCommand appeler** commande. À ce stade simplement afficher une boîte de message indiquant que « FirstCommandPackage à l’intérieur de FirstMenuCommand.FirstCommand.MenuItemCallback() ». Nous verrons comment réellement démarrer le bloc-notes à partir de cette commande dans la section suivante.  
  
## <a name="changing-the-menu-command-handler"></a>Modifier le Gestionnaire de commandes de Menu  
 Maintenant nous allons mettre à jour le Gestionnaire de commandes pour démarrer le bloc-notes.  
  
1.  Arrêter le débogage et revenez à votre instance de travail de Visual Studio. Ouvrez le fichier FirstCommand.cs et ajoutez le code suivant à l’aide d’instruction :  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Recherchez le constructeur de FirstCommand privé. Il s’agit dans lequel la commande est raccordée au service de commande et le Gestionnaire de commandes est spécifié. Remplacez le nom du Gestionnaire de commandes StartNotepad, comme suit :  
  
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
  
3.  Supprimer la méthode MenuItemCallback et ajoutez une méthode StartNotepad qui démarrera simplement le bloc-notes :  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Essayez maintenant. Lorsque vous commencez à déboguer le projet et cliquez sur **outils / appeler FirstCommand**, vous devez voir une instance de bloc-notes s’affiche.  
  
     Vous pouvez utiliser une instance de la <xref:System.Diagnostics.Process> classe pour exécuter n’importe quel fichier exécutable, pas seulement le bloc-notes. Essayer avec calc.exe, par exemple.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Nettoyage de l’environnement expérimental  
 Si vous développez plusieurs extensions, ou explorez juste les résultats avec différentes versions de votre code d’extension, votre environnement expérimental peut-être cesser de fonctionner correctement. Dans ce cas, vous devez exécuter le script de réinitialisation. Il est appelé **réinitialiser l’Instance expérimentale de Visual Studio 2015**, et il est fourni avec le SDK Visual Studio. Ce script supprime toutes les références à vos extensions à partir de l’environnement expérimental, pour que vous puissiez commencer à partir de zéro.  
  
 Vous pouvez accéder à ce script de deux manières :  
  
1.  À partir du bureau, recherchez **réinitialiser l’Instance expérimentale de Visual Studio 2015**.  
  
2.  À partir de la ligne de commande, exécutez ce qui suit :  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Déploiement de votre extension  
 Maintenant que vous avez votre extension de l’outil en cours d’exécution comme vous le souhaitez, il est temps de réfléchir à partager avec vos amis et collègues. C’est facile, à condition qu’ils disposent Visual Studio 2015 est installé. Il vous suffit est leur envoyer le fichier .vsix que vous avez créé. (Veillez à générer dans le mode de mise en production).  
  
 Vous trouverez le fichier .vsix pour cette extension dans le répertoire bin de FirstMenuCommand. Plus précisément, en supposant que vous avez créé la configuration Release, il sera dans :  
  
 **\<répertoire de code > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Pour installer l’extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double-cliquez sur le fichier .vsix, qui permet d’afficher le **programme d’installation VSIX**. Les fichiers sont copiés dans le **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** directory.  
  
 Lorsque votre ami affiche à nouveau Visual Studio, il y trouverez l’extension FirstMenuCommand dans **outils / Extensions et mises à jour**. Il peut atteindre **Extensions et mises à jour** pour désinstaller ou désactiver l’extension, trop.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas vous a montré qu’une petite partie de ce que vous pouvez faire avec une extension Visual Studio. Voici une courte liste d’autres choses (raisonnablement faciles), que vous pouvez faire avec les extensions Visual Studio :  
  
1.  Vous pouvez effectuer bien d’autres choses avec une commande de menu simple :  
  
    1.  Ajouter votre propre icône : [Ajout d’icônes aux commandes de Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modifier le texte de la commande de menu : [modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Ajouter un raccourci du menu à une commande : [liaison des raccourcis clavier aux éléments de Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Ajouter différents types de commandes, menus et barres d’outils : [extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)  
  
3.  Ajouter des fenêtres Outil et d’étendre les fenêtres d’outils intégrés de Visual Studio : [extension et personnalisation de Windows d’outil](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Ajouter des suggestions de code, IntelliSense et éditeurs de code des autres fonctionnalités à un élément existant : [extension de l’éditeur et les Services de langage](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Ajouter des pages de propriété et les Options et paramètres utilisateur vers votre extension : [étendre les propriétés et la fenêtre des propriétés](../extensibility/extending-properties-and-the-property-window.md) et [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md)  
  
 D’autres types d’extensions nécessitent un peu plus de travail, telles que la création d’un nouveau type de projet ([extension des projets](../extensibility/extending-projects.md)), création d’un nouveau type d’éditeur ([création des éditeurs personnalisés et les concepteurs](../extensibility/creating-custom-editors-and-designers.md)), ou implémentation de votre extension dans un interpréteur de commandes isolé : [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)

