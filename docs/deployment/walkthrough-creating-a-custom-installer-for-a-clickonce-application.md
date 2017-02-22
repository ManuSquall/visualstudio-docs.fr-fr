---
title: "Walkthrough: Creating a Custom Installer for a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, custom installer"
  - "installer [ClickOnce], custom"
  - "deploying applications [ClickOnce], custom installer"
  - "InPlaceHostingManager [ClickOnce], custom installer"
  - "custom installer [ClickOnce]"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# Walkthrough: Creating a Custom Installer for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Toute application ClickOnce basée sur un fichier .exe peut être installée en mode silencieux et mise à jour par un programme d'installation personnalisé.  Un programme d'installation personnalisé peut implémenter l'expérience utilisateur personnalisé durant l'installation, notamment les boîtes de dialogue personnalisées pour les opérations de sécurité et de maintenance.  Pour effectuer les opérations d'installation, le programme d'installation personnalisé utilise la classe <xref:System.Deployment.Application.InPlaceHostingManager>.  Cette procédure pas à pas montre comment créer un programme d'installation personnalisé qui installe une application ClickOnce en mode silencieux.  
  
## Composants requis  
  
### Pour créer un programme d'installation d'application ClickOnce personnalisé  
  
1.  Dans votre application ClickOnce, ajoutez des références à System.Deployment et System.Windows.Forms.  
  
2.  Ajoutez une classe nouvelle à votre application et spécifiez un nom de votre choix.  Cette procédure pas à pas utilise le nom `MyInstaller`.  
  
3.  Ajoutez les instructions `Imports` ou `using` suivantes en haut de votre nouvelle classe.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Ajoutez les méthodes suivantes à la classe.  
  
     Ces méthodes appellent des méthodes <xref:System.Deployment.Application.InPlaceHostingManager> pour télécharger le manifeste de déploiement, déclarer les autorisations appropriées, demander à l'utilisateur l'autorisation d'installer, puis télécharger et installer l'application dans le cache ClickOnce.  Un programme d'installation personnalisé peut spécifier qu'une application ClickOnce est pré\-approuvée, ou différer la décision d'approbation à l'appel de méthode <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>.  Ce code pré\-approuve l'application.  
  
    > [!NOTE]
    >  Les autorisations assignées en pré\-approbation ne peuvent pas dépasser les autorisations du code du programme d'installation personnalisé.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Pour tenter l'installation à partir de votre code, appelez la méthode `InstallApplication`.  Par exemple, si vous avez nommé votre classe `MyInstaller`, vous pouvez appeler `InstallApplication` de la façon suivante.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Étapes suivantes  
 Une application ClickOnce peut également ajouter une logique de mise à jour personnalisée, notamment une interface utilisateur personnalisée à afficher lors du processus de mise à jour.  Pour plus d'informations, consultez <xref:System.Deployment.Application.UpdateCheckInfo>.  Une application ClickOnce peut également supprimer l'entrée de menu et le raccourci Démarrer standard, ainsi que l'entrée Ajouter ou supprimer des programmes à l'aide d'un élément `<customUX>`.  Pour plus d'informations, consultez [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md) et <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)