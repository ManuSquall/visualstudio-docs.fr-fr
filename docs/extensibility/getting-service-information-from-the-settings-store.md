---
title: Obtention d’informations de service à partir du magasin de paramètres | Microsoft Docs
description: Découvrez comment utiliser le magasin de paramètres pour rechercher tous les services disponibles ou pour déterminer si un service particulier est installé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900640"
---
# <a name="get-service-information-from-the-settings-store"></a>Récupérer les informations de service à partir du magasin de paramètres
Vous pouvez utiliser le magasin de paramètres pour rechercher tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.

## <a name="to-list-the-available-services"></a>Pour répertorier les services disponibles

1. Créez un projet VSIX nommé `FindServicesExtension` , puis ajoutez une commande personnalisée nommée `FindServicesCommand` . Pour plus d’informations sur la création d’une commande personnalisée, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans *FindServicesCommand. cs*, ajoutez les directives d’utilisation suivantes :

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenez le magasin des paramètres de configuration, puis recherchez le sous-groupe nommé services. Cette collection comprend tous les services disponibles. Dans la `MenuItemCommand` méthode, supprimez le code existant et remplacez-le par ce qui suit :

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

4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

5. Dans l’instance expérimentale, dans le menu **Outils** , cliquez sur **appeler FindServicesCommand**.

     Vous devriez voir une boîte de message répertoriant tous les services.

     Pour vérifier ces paramètres, vous pouvez utiliser l’éditeur du Registre.

## <a name="find-a-specific-service"></a>Rechercher un service spécifique
 Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> méthode pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.

1. Dans le MenuItemCallback du projet que vous avez créé au cours de la procédure précédente, recherchez dans le magasin des paramètres de configuration la `Services` collection qui contient le sous-groupe nommé par le GUID du service. Dans ce cas, nous allons Rechercher le service d’aide.

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

3. Dans l’instance expérimentale, dans le menu **Outils** , cliquez sur **appeler FindServicesCommand**.

     Vous devez voir un message avec le **service d’aide en texte disponible :**  suivi de **true** ou **false**. Pour vérifier ce paramètre, vous pouvez utiliser un éditeur du Registre, comme indiqué dans les étapes précédentes.
