---
title: Obtention d’informations de Service à partir du Store paramètres | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116652"
---
# <a name="getting-service-information-from-the-settings-store"></a>Obtention d’informations de service de la banque de paramètres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser la banque de paramètres pour rechercher tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.  
  
### <a name="to-list-the-available-services"></a>Pour répertorier les services disponibles  
  
1. Créez un projet VSIX nommé FindServicesExtension, puis ajoutez une commande personnalisée nommée FindServicesCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. Dans FindServicesCommand.cs, ajoutez le code suivant à l’aide d’instructions :  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Obtenir la banque de paramètres de configuration, puis recherchez le sous-groupe Services nommé. Cette collection inclut tous les services disponibles. Dans la méthode MenuItemCommand, supprimez le code existant et remplacez-le par ce qui suit :  
  
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
  
## <a name="finding-a-specific-service"></a>Recherche d’un Service spécifique  
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
