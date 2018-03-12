---
title: "À l’aide de la banque de paramètres | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ecb7cf4a40793116159bd2ff8292f0303e3cc46f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-settings-store"></a>À l’aide de la banque de paramètres
Il existe deux types de magasins de paramètres :  
  
-   Paramètres de configuration, qui sont des paramètres de Visual Studio et le VSPackage en lecture seule. Visual Studio fusionne les paramètres de tous les fichiers .pkgdef connus dans le magasin.  
  
-   Paramètres utilisateur, qui sont accessibles en écriture paramètres tels que ceux qui sont affichés sur les pages de la **Options** boîte de dialogue pages de propriétés et certaines autres boîtes de dialogue. Extensions Visual Studio peuvent utiliser pour le stockage local de petites quantités de données.  
  
 Cette procédure pas à pas montre comment lire des données à partir du magasin de paramètre de configuration. Consultez [l’écriture dans le magasin de paramètres utilisateur](../extensibility/writing-to-the-user-settings-store.md) pour une explication de l’écriture dans le magasin de paramètres utilisateur.  
  
## <a name="creating-the-example-project"></a>Création de l’exemple de projet  
 Cette section montre comment créer un projet d’extension simple avec une commande de menu de démonstration.  
  
1.  Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `SettingsStoreExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Maintenant ajouter un modèle d’élément de commande personnalisée nommé **SettingsStoreCommand**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de commande pour **SettingsStoreCommand.cs**. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>À l’aide de la banque de paramètres de Configuration  
 Cette section montre comment détecter et afficher les paramètres de configuration.  
  
1.  Dans le fichier SettingsStorageCommand.cs, ajoutez le code suivant à l’aide des instructions :  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  Dans `MenuItemCallback`, supprimez le corps de la méthode et ajouter ces lignes obtenir le magasin de paramètres de configuration :  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Le <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> est une classe d’assistance gérés via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.  
  
3.  Maintenant déterminer si les outils de Windows Phone sont installées. Le code doit ressembler à ceci :  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Tester le code. Générez le projet et commencez le débogage.  
  
5.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **SettingsStoreCommand d’appeler**.  
  
     Vous devez voir un message indiquant **outils de développement Microsoft Windows Phone :** suivie **True** ou **False**.  
  
 Visual Studio conserve le stockage de paramètres dans le Registre système.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Pour utiliser un éditeur du Registre pour vérifier les paramètres de configuration  
  
1.  Ouvrez Regedit.exe.  
  
2.  Accédez à HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Assurez-vous que vous cherchez à la clé qui contient \14.0Exp_Config\ et pas \14.0_Config\\. Lorsque vous exécutez l’instance expérimentale de Visual Studio, les paramètres de configuration sont dans la ruche de Registre « 14.0Exp_Config ».  
  
3.  Développez le nœud \Installed Products\. Si le message dans les étapes précédentes **Microsoft Windows Phone Developer Tools installé : True**, puis \Installed Products\ doit contenir un nœud d’outils de développement Microsoft Windows Phone. Si le message est **Microsoft Windows Phone Developer Tools installé : False**, \Installed Products\ ne doit pas contenir un nœud d’outils de développement Microsoft Windows Phone.