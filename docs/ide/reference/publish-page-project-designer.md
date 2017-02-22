---
title: "Page Publier, Concepteur de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Concepteur de projets, page Publier"
  - "page Publier dans le Concepteur de projets"
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Page Publier, Concepteur de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement ClickOnce.  
  
 Pour accéder à la boîte de dialogue **Publier**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Publier**.  
  
> [!NOTE]
>  Certaines des propriétés ClickOnce décrites ici peuvent également être définies dans l’**AssistantPublication**, accessibles à partir du menu **Générer** ou en cliquant sur le bouton **AssistantPublication** dans cette page.  
  
## Liste UIElement  
 **Emplacement du dossier de publication**  
 Spécifie l’emplacement où l’application est publiée. Peut être un chemin de lecteur \(`C:\deploy\myapplication`\), un partage de fichiers \(`\\server\myapplication`\), un serveur FTP \(`ftp://ftp.microsoft.com/myapplication`\) ou un site web \(`http://www.microsoft.com/myapplication`\). Notez que du texte doit figurer dans la zone **Emplacement de publication** pour que le bouton de navigation \(**...**\) fonctionne.  
  
 Par défaut, l’emplacement de publication est `http://localhost/<projectname>/` si vous avez installé IIS, ou le répertoire `publish\` si vous n’avez pas installé IIS. Si votre ordinateur exécute Windows Vista, la valeur par défaut est toujours le répertoire `publish\`, qu’IIS soit installé ou non.  
  
 **URL du dossier d’installation**  
 Facultatif. Spécifie un site web auquel les utilisateurs accèdent pour installer l’application. Cette URL est nécessaire uniquement si elle diffère de l’**Emplacement de publication**, par exemple quand l’application est publiée sur un serveur intermédiaire.  
  
 **Mode et paramètres d'installation**  
 Détermine si l’application est exécutée directement à partir de l’**Emplacement de publication** \(quand l’option **L’application est disponible en ligne uniquement** est sélectionnée\) ou si elle est installée et ajoutée au menu **Démarrer** et à l’élément **Ajouter ou supprimer des programmes** du **Panneau de configuration** \(quand l’option **L’application est également disponible hors connexion** est sélectionnée\).  
  
 Pour les applications du navigateur web WPF, l’option **L’application est également disponible hors connexion** est désactivée, car ces applications sont disponibles uniquement en ligne.  
  
 **Fichiers de l'application**  
 Ouvre la [Application Files Dialog Box](http://msdn.microsoft.com/fr-fr/b06dff3a-b87a-4caf-996b-7a4acf8137a8), qui permet de spécifier comment et où les fichiers sont installés.  
  
 **Conditions préalables**  
 Ouvre la [Composants requis, boîte de dialogue](../../ide/reference/prerequisites-dialog-box.md), qui permet de spécifier les composants requis, tels que le .NET Framework, à installer avec l’application.  
  
 **Mises à jour**  
 Ouvre la [Application Updates Dialog Box](http://msdn.microsoft.com/fr-fr/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), qui permet de spécifier le comportement de mise à jour de l’application. Non disponible quand l’option **L’application est disponible en ligne uniquement** est sélectionnée.  
  
 **Options**  
 Ouvre la [Publish Options Dialog Box](http://msdn.microsoft.com/fr-fr/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), qui permet de spécifier des options de publication avancées.  
  
 **Version de publication**  
 Définit le numéro de version de publication de l’application. Quand vous changez le numéro de version, l’application est publiée en tant que mise à jour. Chaque partie de la version de publication \(**Principale**, **Secondaire**, **Build**, **Révision**\) peut avoir une valeur maximale de 65355 \(<xref:System.UInt16.MaxValue>\), la valeur maximale autorisée par <xref:System.Version>.  
  
 Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.  
  
 **Incrémenter automatiquement la révision avec chaque publication**  
 Facultatif. Quand cette option est activée \(valeur par défaut\), la partie **Révision** du numéro de version de publication est incrémentée d’une unité chaque fois que l’application est publiée. Cela entraîne la publication de l’application en tant que mise à jour.  
  
 **Assistant Publication**  
 Ouvre [Publish Wizard](http://msdn.microsoft.com/fr-fr/fc6abebd-13d6-48e4-a567-fbc52dad0872). L’exécution complète de l’Assistant Publication a le même effet que l’exécution de la commande **Publier** dans le menu **Générer**.  
  
 **Publier maintenant**  
 Publie l’application à l’aide des paramètres actuels. Équivaut au bouton **Terminer** situé dans l’**AssistantPublication**.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [How to: Specify Where Visual Studio Copies the Files](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [How to: Specify the Location Where End Users Will Install From](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [How to: Specify a Link for Technical Support](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [How to: Specify the ClickOnce Offline or Online Install Mode](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [How to: Enable AutoStart for CD Installations](../Topic/How%20to:%20Enable%20AutoStart%20for%20CD%20Installations.md)   
 [How to: Set the ClickOnce Publish Version](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [How to: Automatically Increment the ClickOnce Publish Version](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [How to: Specify Which Files Are Published by ClickOnce](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [How to: Manage Updates for a ClickOnce Application](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)   
 [How to: Change the Publish Language for a ClickOnce Application](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [How to: Specify a Start Menu Name for a ClickOnce Application](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)