---
title: "Obtention d&#39;informations de Service de la banque de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Obtention d&#39;informations de Service de la banque de param&#232;tres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le stockage de paramètres pour trouver tous les services disponibles ou pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.  
  
### Pour répertorier les services disponibles  
  
1.  Créez un projet VSIX nommé FindServicesExtension, puis ajoutez une commande personnalisée nommée FindServicesCommand. Pour plus d'informations sur la création d'une commande personnalisée, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  Dans FindServicesCommand.cs, ajoutez les instructions using :  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  Obtenir le magasin de paramètres de configuration, puis recherchez le sous\-groupe nommé Services. Cette collection inclut tous les services disponibles. Dans la méthode MenuItemCommand, supprimez le code existant et remplacez\-le par le code suivant :  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  Générez le projet et commencez le débogage. L'instance expérimentale s'affiche.  
  
5.  Dans l'instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand appeler**.  
  
     Vous devez voir une boîte de message répertoriant tous les services.  
  
     Pour vérifier ces paramètres, vous pouvez utiliser l'Éditeur du Registre.  
  
## Recherche d'un Service spécifique  
 Vous pouvez également utiliser le <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> méthode pour déterminer si un service particulier est installé. Vous devez connaître le type de la classe de service.  
  
1.  MenuItemCallback du projet que vous avez créé dans la procédure précédente, la banque de paramètres de configuration pour rechercher la `Services` collection qui possède le sous\-groupe nommé par le GUID du service. Dans ce cas, nous allons pour le service d'aide.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  Générez le projet et commencez le débogage.  
  
3.  Dans l'instance expérimentale, sur le **outils** menu, cliquez sur **FindServicesCommand appeler**.  
  
     Vous devez voir un message avec le texte **aide Service disponible :**  suivie **True** ou **False**. Pour vérifier ce paramètre, vous pouvez utiliser un éditeur de Registre, comme indiqué dans les étapes précédentes.