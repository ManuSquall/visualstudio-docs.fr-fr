---
title: Obtenir des informations sur le service à partir du magasin Paramètres Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711371"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtenez des informations de service à partir du magasin de paramètres
Vous pouvez utiliser le magasin de paramètres pour trouver tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de classe de service.

## <a name="to-list-the-available-services"></a>Énumérer les services disponibles

1. Créez un projet `FindServicesExtension` VSIX nommé, puis `FindServicesCommand`ajoutez une commande personnalisée nommée . Pour plus d’informations sur la façon de créer une commande personnalisée, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans *FindServicesCommand.cs*, ajouter ce qui suit en utilisant des directives:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenez le stockage des paramètres de configuration, puis trouvez la sous-collection nommée Services. Cette collection comprend tous les services disponibles. Dans `MenuItemCommand` la méthode, supprimez le code existant et remplacez-le par les éléments suivants :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

5. Dans le cas expérimental, sur le menu **Tools,** cliquez sur **Invoke FindServicesCommand**.

     Vous devriez voir une boîte de message énumérant tous les services.

     Pour vérifier ces paramètres, vous pouvez utiliser l’éditeur du registre.

## <a name="find-a-specific-service"></a>Trouver un service spécifique
 Vous pouvez également <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> utiliser la méthode pour déterminer si un service particulier est installé. Vous devez connaître le type de classe de service.

1. Dans le MenuItemCallback du projet que vous avez créé dans `Services` la procédure précédente, rechercher les paramètres de configuration stocker pour la collection qui a la sous-collection nommée par le GUID du service. Dans ce cas, nous allons chercher le service d’aide.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Générez le projet et commencez le débogage.

3. Dans le cas expérimental, sur le menu **Tools,** cliquez sur **Invoke FindServicesCommand**.

     Vous devriez voir un message avec le service **d’aide** texte disponible: suivi par **True** ou **False**. Pour vérifier ce paramètre, vous pouvez utiliser un éditeur de registre, comme indiqué dans les étapes précédentes.
