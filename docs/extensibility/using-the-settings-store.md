---
title: À l’aide de la Store paramètres | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4487020232b897d62711bb9053f43ad2ef2694f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338108"
---
# <a name="using-the-settings-store"></a>Utilisation de la banque de paramètres
Il existe deux types de magasins de paramètres :

- Paramètres de configuration, qui sont des paramètres de Visual Studio et VSPackage en lecture seule. Visual Studio fusionne les paramètres à partir de tous les fichiers .pkgdef connus dans ce magasin.

- Paramètres utilisateur, qui sont des paramètres accessible en écriture, telles que celles qui sont affichées dans les pages dans le **Options** boîte de dialogue pages de propriétés et certaines autres boîtes de dialogue. Extensions Visual Studio peuvent utiliser pour le stockage local de petites quantités de données.

  Cette procédure pas à pas montre comment lire des données à partir du magasin de paramètre de configuration. Consultez [écriture dans le Store de paramètres utilisateur](../extensibility/writing-to-the-user-settings-store.md) pour une explication de l’écriture dans la banque de paramètres utilisateur.

## <a name="creating-the-example-project"></a>Création de l’exemple de projet
 Cette section montre comment créer un projet d’extension simple avec une commande de menu pour la démonstration.

1. Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contiendra les ressources de l’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `SettingsStoreExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.

2. Ajoutez maintenant un modèle d’élément de commande personnalisée nommé **SettingsStoreCommand**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour **SettingsStoreCommand.cs**. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>À l’aide du Store de paramètres de Configuration
 Cette section montre comment détecter et d’afficher les paramètres de configuration.

1. Dans le fichier SettingsStorageCommand.cs, ajoutez le code suivant à l’aide d’instructions :

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. Dans `MenuItemCallback`, supprimez le corps de la méthode et ajouter ces lignes Obtient la banque de paramètres de configuration :

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Le <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> est une classe d’assistance managée via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> service.

3. Maintenant, cherchez si les outils de Windows Phone sont installées. Le code doit ressembler à ceci :

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

4. Tester le code. Générez le projet et commencez le débogage.

5. Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **SettingsStoreCommand appeler**.

    Vous devez voir un message indiquant **outils de développement de Microsoft Windows Phone :** suivie **True** ou **False**.

   Visual Studio conserve la banque de paramètres dans le Registre système.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Pour utiliser un éditeur du Registre pour vérifier les paramètres de configuration

1. Ouvrez Regedit.exe.

2. Accédez à HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.

    > [!NOTE]
    > Assurez-vous que vous examinez la clé qui contient \14.0Exp_Config\ et pas \14.0_Config\\. Lorsque vous exécutez l’instance expérimentale de Visual Studio, les paramètres de configuration sont dans la ruche de Registre « 14.0Exp_Config ».

3. Développez le nœud \Installed Products\. Si le message dans les étapes précédentes est **Microsoft Windows Phone Developer Tools installé : True**, alors \Installed Products\ doit contenir un nœud d’outils de développement de Microsoft Windows Phone. Si le message est **Microsoft Windows Phone Developer Tools installé : False**, alors \Installed Products\ ne doit pas contenir un nœud d’outils de développement de Microsoft Windows Phone.