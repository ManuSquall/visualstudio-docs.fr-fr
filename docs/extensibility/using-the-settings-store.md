---
title: Utilisation de la Banque de paramètres | Microsoft Docs
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
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632594"
---
# <a name="using-the-settings-store"></a>Utilisation de la banque de paramètres
Il existe deux types de banques de paramètres :

- Paramètres de configuration, qui sont des paramètres Visual Studio et VSPackage en lecture seule. Visual Studio fusionne les paramètres de tous les fichiers. pkgdef connus dans ce magasin.

- Les paramètres utilisateur, qui sont des paramètres inscriptibles, tels que ceux qui sont affichés sur les pages de la boîte de dialogue **options** , les pages de propriétés et certaines autres boîtes de dialogue. Les extensions Visual Studio peuvent les utiliser pour le stockage local de petites quantités de données.

  Cette procédure pas à pas montre comment lire des données à partir du magasin des paramètres de configuration. Consultez [écriture dans le magasin des paramètres utilisateur](../extensibility/writing-to-the-user-settings-store.md) pour obtenir une explication sur la façon d’écrire dans le magasin des paramètres utilisateur.

## <a name="creating-the-example-project"></a>Création de l’exemple de projet
 Cette section montre comment créer un projet d’extension simple avec une commande de menu pour la démonstration.

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX qui contiendra les ressources d’extension. Créez un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX nommé `SettingsStoreExtension`. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous  **C# Visual/extensibilité**.

2. Ajoutez maintenant un modèle d’élément de commande personnalisé nommé **SettingsStoreCommand**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C# /extensibilité** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par **SettingsStoreCommand.cs**. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Utilisation du magasin des paramètres de configuration
 Cette section montre comment détecter et afficher les paramètres de configuration.

1. Dans le fichier SettingsStorageCommand.cs, ajoutez les directives d’utilisation suivantes :

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. Dans `MenuItemCallback`, supprimez le corps de la méthode, puis ajoutez ces lignes pour accéder au magasin des paramètres de configuration :

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Le <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> est une classe d’assistance managée sur le service <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>.

3. À présent, déterminez si Windows Phone outils sont installés. Le code doit ressembler à ceci :

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

4. Testez le code. Générez le projet et commencez le débogage.

5. Dans l’instance expérimentale, dans le menu **Outils** , cliquez sur **appeler SettingsStoreCommand**.

    Vous devriez voir une boîte de message indiquant que **Microsoft Windows Phone outils de développement :** suivi de **true** ou **false**.

   Visual Studio conserve la Banque de paramètres dans le registre système.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Pour utiliser un éditeur du Registre afin de vérifier les paramètres de configuration

1. Ouvrez regedit. exe.

2. Accédez à HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\.

    > [!NOTE]
    > Vérifiez que vous examinez la clé qui contient \14.0Exp_Config\ et non \14.0_Config \\. Lorsque vous exécutez l’instance expérimentale de Visual Studio, les paramètres de configuration se trouvent dans la ruche de Registre « 14.0 Exp_Config ».

3. Développez le nœud \Installed Products \. Si le message de la procédure précédente est **Microsoft Windows Phone outils de développement installé : true**, \Installed Products \ doit contenir un nœud microsoft Windows Phone outils de développement. Si le message est **Microsoft Windows Phone outils de développement installé : false**, alors \Installed Products \ ne doit pas contenir de nœud microsoft Windows Phone outils de développement.
