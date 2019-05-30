---
title: Obtention d’informations de Service à partir du Store paramètres | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f65fe81d1b2382df3847c2cfdc0b8ffbfff5662
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342438"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtenir des informations de service à partir de la banque de paramètres
Vous pouvez utiliser la banque de paramètres pour rechercher tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.

## <a name="to-list-the-available-services"></a>Pour répertorier les services disponibles

1. Créez un projet VSIX nommé `FindServicesExtension` , puis ajoutez une commande personnalisée nommée `FindServicesCommand`. Pour plus d’informations sur la création d’une commande personnalisée, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans *FindServicesCommand.cs*, ajoutez le code suivant à l’aide d’instructions :

    ```vb
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenir la banque de paramètres de configuration, puis recherchez le sous-groupe Services nommé. Cette collection inclut tous les services disponibles. Dans le `MenuItemCommand` (méthode), supprimez le code existant et remplacez-le par le code suivant :

    ```
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

5. Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand appeler**.

     Vous devez voir une boîte de message répertoriant tous les services.

     Pour vérifier ces paramètres, vous pouvez utiliser l’Éditeur du Registre.

## <a name="find-a-specific-service"></a>Rechercher un service spécifique
 Vous pouvez également utiliser le <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> méthode pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.

1. Dans le MenuItemCallback du projet que vous avez créé dans la procédure précédente, recherchez la banque de paramètres de configuration pour le `Services` collection qui possède le sous-groupe nommé par le GUID du service. Dans ce cas, nous allons pour le service d’aide.

    ```
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

3. Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand appeler**.

     Vous devez voir un message avec le texte **aide Service Available :** suivie **True** ou **False**. Pour vérifier ce paramètre, vous pouvez utiliser un éditeur du Registre, comme indiqué dans les étapes précédentes.