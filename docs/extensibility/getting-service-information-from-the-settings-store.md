---
title: "Obtention d’informations sur le Service à partir du magasin de paramètres | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fdb7e95a4a4379dfbab3e56cc21e9515bb23ec0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-service-information-from-the-settings-store"></a>Lors de l’obtention des informations de Service à partir du magasin de paramètres
Vous pouvez utiliser le stockage de paramètres pour rechercher tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.  
  
### <a name="to-list-the-available-services"></a>Pour répertorier les services disponibles  
  
1.  Créez un projet VSIX nommé FindServicesExtension, puis ajoutez une commande personnalisée nommée FindServicesCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  Dans FindServicesCommand.cs, ajoutez le code suivant à l’aide des instructions :  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Obtenir le magasin de paramètres de configuration, puis recherchez le sous-groupe nommé Services. Cette collection contient tous les services disponibles. Dans la méthode MenuItemCommand, supprimez le code existant et remplacez-le par les éléments suivants :  
  
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
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
5.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand d’appeler**.  
  
     Vous devez voir une boîte de message qui répertorie tous les services.  
  
     Pour vérifier ces paramètres, vous pouvez utiliser l’Éditeur du Registre.  
  
## <a name="finding-a-specific-service"></a>Recherche d’un Service spécifique  
 Vous pouvez également utiliser le <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> méthode pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.  
  
1.  Dans MenuItemCallback du projet que vous avez créé dans la procédure précédente, recherche dans le magasin de paramètres de configuration pour le `Services` collection qui possède le sous-groupe nommé par le GUID du service. Dans ce cas, nous allons examiner pour le service d’aide.  
  
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
  
2.  Générez le projet et commencez le débogage.  
  
3.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand d’appeler**.  
  
     Vous devez voir un message avec le texte **aider les services disponibles :** suivie **True** ou **False**. Pour vérifier ce paramètre, vous pouvez utiliser un éditeur du Registre, comme indiqué dans les étapes précédentes.