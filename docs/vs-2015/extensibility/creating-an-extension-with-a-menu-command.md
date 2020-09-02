---
title: Création d’une extension à l’aide d’une commande de menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572885"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Création d’une extension avec une commande de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une extension avec une commande de menu qui lance le bloc-notes.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Création d’une commande de menu  
  
1. Créez un projet VSIX nommé **FirstMenuCommand**. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous **Visual C#/extensibilité**.  
  
2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **FirstCommand**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par **FirstCommand.cs**.  
  
3. Générez le projet et commencez le débogage.  
  
     L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
4. Dans l’instance expérimentale, ouvrez la fenêtre  **Outils/extensions et mises à jour** . Vous devez voir l’extension **FirstMenuCommand** ici. (Si vous ouvrez **extensions et mises à jour** dans votre instance de Visual Studio qui fonctionne, vous ne voyez pas **FirstMenuCommand**).  
  
     Maintenant, accédez au menu **Outils** de l’instance expérimentale. La commande **Invoke FirstCommand** doit s’afficher. À ce stade, il affiche simplement une boîte de message indiquant « FirstCommandPackage dans FirstMenuCommand. FirstCommand. MenuItemCallback () ». Nous verrons comment démarrer le bloc-notes à partir de cette commande dans la section suivante.  
  
## <a name="changing-the-menu-command-handler"></a>Modification du gestionnaire de commandes de menu  
 À présent, nous allons mettre à jour le gestionnaire de commandes pour démarrer le bloc-notes.  
  
1. Arrêtez le débogage et revenez à votre instance de travail de Visual Studio. Ouvrez le fichier FirstCommand.cs et ajoutez l’instruction using suivante :  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Recherchez le constructeur Private FirstCommand. C’est là que la commande est raccordée au service de commande et que le gestionnaire de commandes est spécifié. Remplacez le nom du gestionnaire de commandes par StartNotepad, comme suit :  
  
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
  
3. Supprimez la méthode MenuItemCallback et ajoutez une méthode StartNotepad qui démarre simplement le bloc-notes :  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. Essayez maintenant. Quand vous commencez à déboguer le projet et que vous cliquez sur **Outils/appeler FirstCommand**, une instance du bloc-notes doit apparaître.  
  
     Vous pouvez utiliser une instance de la <xref:System.Diagnostics.Process> classe pour exécuter n’importe quel exécutable, pas seulement le bloc-notes. Essayez-le avec calc.exe, par exemple.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Nettoyage de l’environnement expérimental  
 Si vous développez plusieurs extensions ou explorez uniquement les résultats avec des versions différentes de votre code d’extension, votre environnement expérimental peut cesser de fonctionner comme il le devrait. Dans ce cas, vous devez exécuter le script de réinitialisation. Elle est appelée **Réinitialiser l’instance expérimentale de Visual studio 2015**, et elle est fournie dans le cadre du kit de développement logiciel (SDK) Visual Studio. Ce script supprime toutes les références à vos extensions de l’environnement expérimental, de sorte que vous pouvez commencer à partir de zéro.  
  
 Vous pouvez accéder à ce script de deux manières :  
  
1. À partir du bureau, recherchez **Réinitialiser l’instance expérimentale de Visual Studio 2015**.  
  
2. À partir de la ligne de commande, exécutez ce qui suit :  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Déploiement de votre extension  
 Maintenant que votre extension d’outil fonctionne comme vous le souhaitez, il est temps de réfléchir au partage avec vos amis et collègues. C’est facile, à condition que Visual Studio 2015 soit installé. Il vous suffit de leur envoyer le fichier. vsix que vous avez créé. (Veillez à le générer en mode release.)  
  
 Vous pouvez trouver le fichier. VSIX pour cette extension dans le répertoire bin FirstMenuCommand. En particulier, en supposant que vous ayez créé la configuration Release, elle sera dans :  
  
 **\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix**  
  
 Pour installer l’extension, votre ami doit fermer toutes les instances ouvertes de Visual Studio, puis double-cliquer sur le fichier. vsix, qui affiche le **programme d’installation VSIX**. Les fichiers sont copiés dans le répertoire **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**  
  
 Quand votre ami rétablit Visual Studio, il trouve l’extension FirstMenuCommand dans **Outils/extensions et mises à jour**. Il peut également accéder à **extensions et mises à jour** pour désinstaller ou désactiver l’extension.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas vous a montré une petite partie de ce que vous pouvez faire avec une extension Visual Studio. Voici une brève liste d’autres choses (raisonnablement faciles) que vous pouvez faire avec les extensions Visual Studio :  
  
1. Vous pouvez faire beaucoup d’autres choses avec une simple commande de menu :  
  
   1. Ajouter votre propre icône : [Ajout d’icônes aux commandes de menu](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Modifier le texte de la commande de menu : [modification du texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Ajouter un raccourci de menu à une commande : [liaison de raccourcis clavier à des éléments de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Ajoutez différents types de commandes, de menus et de barres d’outils : [extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)  
  
3. Ajoutez des fenêtres outil et étendez les fenêtres Outil Visual Studio intégrées : [extension et personnalisation des fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Ajouter IntelliSense, des suggestions de code et d’autres fonctionnalités aux éditeurs de code existants : [extension de l’éditeur et des services de langage](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Ajouter des options et des pages de propriétés et des paramètres utilisateur à votre extension : [extension des propriétés et de la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md) et [extension des paramètres et des options utilisateur](../extensibility/extending-user-settings-and-options.md)  
  
   D’autres types d’extensions nécessitent un peu plus de travail, par exemple la création d’un nouveau type de projet ([extension de projets](../extensibility/extending-projects.md)), la création d’un nouveau type d’éditeur ([création d’éditeurs et de concepteurs personnalisés](../extensibility/creating-custom-editors-and-designers.md)) ou l’implémentation de votre extension dans un interpréteur de commandes isolé : [Visual Studio isolated Shell](../extensibility/visual-studio-isolated-shell.md)
