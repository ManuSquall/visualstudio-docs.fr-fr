---
title: Utilisation du magasin Paramètres Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698515"
---
# <a name="using-the-settings-store"></a>Utilisation de la banque de paramètres
Il existe deux types de magasins de réglages :

- Paramètres de configuration, qui sont des paramètres Visual Studio et VSPackage lus uniquement. Visual Studio fusionne les paramètres de tous les fichiers .pkgdef connus dans ce magasin.

- Paramètres de l’utilisateur, qui sont des paramètres écrivants tels que ceux qui sont affichés sur les pages de la boîte de dialogue **Options,** pages de propriété, et certaines autres boîtes de dialogue. Les extensions Visual Studio peuvent les utiliser pour le stockage local de petites quantités de données.

  Ce pas-là montre comment lire les données du magasin de configuration. Voir [l’écriture sur le Magasin des paramètres de l’utilisateur](../extensibility/writing-to-the-user-settings-store.md) pour une explication de la façon d’écrire au magasin de paramètres de l’utilisateur.

## <a name="creating-the-example-project"></a>Création du projet d’exemple
 Cette section montre comment créer un projet d’extension simple avec une commande de menu pour la démonstration.

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX qui contiendra les actifs d’extension. Créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un projet `SettingsStoreExtension`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le **dialogue du nouveau projet** sous Visual C ' / **Extensibility**.

2. Maintenant, ajoutez un modèle d’élément de commande personnalisé nommé **SettingsStoreCommand**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C / Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour **SettingsStoreCommand.cs**. Pour plus d’informations sur la façon de créer une commande personnalisée, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Utilisation du magasin Paramètres de Configuration
 Cette section montre comment détecter et afficher les paramètres de configuration.

1. Dans le fichier SettingsStorageCommand.cs, ajoutez les directives suivantes à l’aide de directives :

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. Dans `MenuItemCallback`, supprimer le corps de la méthode, et ajouter ces lignes obtenir le stockage des paramètres de configuration:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> s’agit d’une <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> classe d’aide gérée sur le service.

3. Maintenant, découvrez si Windows Phone Tools sont installés. Le code devrait ressembler à ceci:

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

5. Dans le cas expérimental, sur le menu **Tools,** cliquez sur **Invoke SettingsStoreCommand**.

    Vous devriez voir une boîte de message disant **Microsoft Windows Phone Developer Tools:** suivie par **True** ou **False**.

   Visual Studio conserve le magasin de paramètres dans le registre du système.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Utiliser un éditeur de registre pour vérifier les paramètres de configuration

1. Ouvrez Regedit.exe.

2. Naviguez vers HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-14.0Exp_Config-InstalledProducts\\.

    > [!NOTE]
    > Assurez-vous que vous regardez la clé qui contient 14,0Exp_Config et non pas 14,0_Config\\. Lorsque vous exécutez l’instance expérimentale de Visual Studio, les paramètres de configuration sont dans la ruche de registre "14.0Exp_Config".

3. Élargissez le nœud « Produits installés ». Si le message dans les étapes précédentes est **Microsoft Windows Phone Developer Tools Installé: Vrai**, puis «Produits installés» devrait contenir un nœud Microsoft Windows Phone Developer Tools. Si le message est **Microsoft Windows Phone Developer Tools Installé: Faux,** puis «Produits installés» ne devrait pas contenir un nœud Microsoft Windows Phone Developer Tools.
