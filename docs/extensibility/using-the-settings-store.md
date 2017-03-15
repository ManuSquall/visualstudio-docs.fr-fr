---
title: "&#192; l&#39;aide de la banque de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Stockage de paramètres, à l'aide de"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# &#192; l&#39;aide de la banque de param&#232;tres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe deux types de magasins de paramètres :  
  
-   Paramètres de configuration, qui sont des paramètres de Visual Studio et VSPackage en lecture seule. Visual Studio fusionne les paramètres à partir de tous les fichiers connus .pkgdef dans ce magasin.  
  
-   Paramètres de l'utilisateur qui sont des paramètres accessible en écriture, telles que celles qui figurent sur les pages de la **Options** boîte de dialogue pages de propriétés et certaines autres boîtes de dialogue. Extensions Visual Studio peuvent utiliser pour le stockage local de petites quantités de données.  
  
 Cette procédure pas à pas montre comment lire des données à partir du magasin de paramètre de configuration. Consultez [Écriture dans le magasin de paramètres utilisateur](../extensibility/writing-to-the-user-settings-store.md) pour obtenir une explication de l'écriture dans le magasin de paramètres utilisateur.  
  
## Création de l'exemple de projet  
 Cette section montre comment créer un projet d'extension simple avec une commande de menu pour la démonstration.  
  
1.  Chaque extension de Visual Studio démarre avec un projet de déploiement VSIX qui contient les composants d'extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `SettingsStoreExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Ajoutez maintenant un modèle d'élément commande personnalisée nommé **SettingsStoreCommand**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **SettingsStoreCommand.cs**. Pour plus d'informations sur la création d'une commande personnalisée, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## À l'aide de la banque de paramètres de Configuration  
 Cette section montre comment détecter et afficher les paramètres de configuration.  
  
1.  Dans le fichier SettingsStorageCommand.cs, ajoutez le code suivant à l'aide des instructions :  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  Dans `MenuItemCallback`, supprimez le corps de la méthode et ajoutez ces lignes obtenir le magasin de paramètres de configuration :  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Le <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> est une classe gérée d'aide sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3.  Maintenant savoir si les outils de Windows Phone sont installées. Le code doit ressembler à ceci :  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  Tester le code. Générez le projet et commencez le débogage.  
  
5.  Dans l'instance expérimentale, sur le **outils** menu, cliquez sur **SettingsStoreCommand appeler**.  
  
     Vous devez voir un message indiquant **Outils de développement Microsoft Windows Phone :**  suivie **True** ou **False**.  
  
 Visual Studio conserve la banque de paramètres dans le Registre système.  
  
#### Pour utiliser un éditeur de Registre pour vérifier les paramètres de configuration  
  
1.  Ouvrez Regedit.exe.  
  
2.  Accédez à HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\.  
  
    > [!NOTE]
    >  Assurez\-vous que vous examinez la clé qui contient \\14.0Exp\_Config\\ et non \\14.0\_Config\\. Lorsque vous exécutez l'instance expérimentale de Visual Studio, les paramètres de configuration sont dans la ruche de Registre « 14.0Exp\_Config ».  
  
3.  Développez le nœud \\Installed Products\\. Si le message dans les étapes précédentes **Microsoft Windows Phone Developer Tools installé : True**, puis \\Installed Products\\ doit contenir un nœud Outils de développement Microsoft Windows Phone. Si le message est **Microsoft Windows Phone Developer Tools installé : False**, \\Installed Products\\ ne doit pas contenir un nœud Outils de développement Microsoft Windows Phone.