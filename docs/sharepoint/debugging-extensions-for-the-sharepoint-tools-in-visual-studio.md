---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  Vous pouvez déboguer des extensions d'outils SharePoint dans l'instance expérimentale ou l'instance normale de Visual Studio.  Si vous devez résoudre les problèmes liés au comportement d'une extension, vous pouvez également modifier les valeurs de Registre pour afficher d'autres informations d'erreur et configurer la manière dont Visual Studio exécute les commandes SharePoint.  
  
## Débogage d'extensions dans une instance expérimentale de Visual Studio  
 Pour protéger votre environnement de développement Visual Studio de toute corruption accidentelle provoquée par des extensions non testées, le Kit de développement Visual Studio SDK fournit une autre instance Visual Studio appelée *instance expérimentale*, que vous pouvez utiliser pour installer et tester les extensions.  Vous développez de nouvelles extensions à l'aide de l'instance normale de Visual Studio, mais vous les déboguez et les exécutez dans l'instance expérimentale.  Pour plus d'informations, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
 Si vous utilisez un projet VSIX pour déployer votre extension, et que le projet VSIX est le projet de démarrage dans votre solution, Visual Studio installe et exécute automatiquement l'extension dans l'instance expérimentale lorsque vous déboguez votre solution.  Le projet de démarrage est le projet qui démarre lorsque vous déboguez une solution contenant plusieurs projets.  Pour plus d'informations sur l'utilisation d'un projet de VSIX afin de déployer votre extension, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  Pour plus d'informations sur les projets de démarrage, consultez [Comment : définir des projets de démarrage](http://msdn.microsoft.com/fr-fr/31465836-0911-48db-a5d9-e456b635e970).  
  
 Pour obtenir des exemples qui illustrent le mode de débogage des différents types d'extensions dans l'instance expérimentale de Visual Studio, consultez les procédures pas à pas suivantes :  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Débogage d'extensions dans l'instance normale de Visual Studio  
 Si vous souhaitez déboguer votre projet d'extension dans l'instance normale de Visual Studio, commencez par installer l'extension dans l'instance normale.  Ensuite, attachez le débogueur à un deuxième processus Visual Studio.  Une fois que vous avez terminé, vous pouvez supprimer l'extension afin qu'elle ne se charge plus sur l'ordinateur de développement.  
  
#### Pour installer l'extension  
  
1.  Fermez toutes les instances de Visual Studio.  
  
2.  Dans le dossier de sortie de la génération pour le projet d'extension, ouvrez le fichier .vsix en double\-cliquant dessus ou en ouvrant le menu contextuel puis en choisissant **Ouvrir**:  
  
3.  Dans la boîte de dialogue **Programme d'installation des extensions Visual Studio** , choisissez l'édition de Visual Studio dans laquelle vous voulez installer l'extension, puis cliquez sur le bouton **Installer**.  
  
     Visual Studio installe les fichiers d'extension dans %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*.  Les trois derniers dossiers de ce chemin d'accès sont définis à partir des éléments `Author`, `Name` et `Version` dans le fichier extension.vsixmanifest pour l'extension.  
  
4.  Une fois que Visual Studio a installé l'extension, cliquez sur **Fermer**.  
  
#### Pour déboguer l'extension  
  
1.  Démarrez Visual Studio avec les privilèges d'administrateur et ouvrez le projet d'extension.  Les étapes suivantes font référence à cette instance de Visual Studio comme la *première instance*.  
  
2.  Démarrez une autre instances de Visual Studio avec les privilèges d'administrateur.  Les étapes suivantes font référence à cette instance de Visual Studio comme la *deuxième instance*.  
  
3.  Basculez vers la première instance de Visual Studio.  
  
4.  Dans la barre de menu, choisissez **Débogage**, **Attacher au processus**.  
  
5.  Dans la liste **Processus disponibles**, choisissez devenv.exe.  Cette entrée fait référence à la deuxième instance de Visual Studio, c'est\-à\-dire celle dans laquelle vous souhaitez déboguer votre extension de projet.  
  
6.  Cliquez sur **Attacher**.  
  
     Visual Studio exécute le projet d'extension en mode débogage.  
  
7.  Basculez vers la deuxième instance de Visual Studio.  
  
8.  Créez un projet SharePoint qui charge votre extension.  Par exemple, si vous déboguez une extension pour des éléments de projet de définition de liste, créez un projet **Définition de liste**.  
  
9. Exécutez les étapes requises pour tester votre code d'extension.  
  
10. Lorsque vous avez terminé le débogage de l'extension, fermez la deuxième instance de Visual Studio.  
  
#### Pour supprimer l'extension  
  
1.  Dans Visual Studio, dans la barre de menus, sélectionnez **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, choisissez le nom de l'extension, puis cliquez sur **Désinstaller**.  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur **Oui** pour confirmer que vous voulez désinstaller l'extension.  
  
4.  Cliquez sur le bouton **Redémarrer maintenant** pour terminer la désinstallation.  
  
## Débogage des commandes SharePoint  
 Si vous souhaitez déboguer une commande SharePoint qui fait partie d'une extension d'outils SharePoint, vous devez attacher le débogueur au processus vssphost4.exe.  Il s'agit d'un processus hôte 64 bits qui exécute des commandes SharePoint.  Pour plus d'informations sur les commandes SharePoint et vssphost4.exe, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### Pour attacher le débogueur au processus vssphost4.exe  
  
1.  Commencez à déboguer votre extension dans l'instance expérimentale ou l'instance standard de Visual Studio en suivant les instructions ci\-dessus.  
  
2.  Dans l'instance de Visual Studio où vous exécutez le débogueur, dans la barre menu, choisissez **Déboguer**, **Attacher au processus**.  
  
3.  Dans la liste de **Processus disponibles**, choisissez vssphost.exe.  
  
    > [!NOTE]  
    >  Si vssphost.exe ne s'affiche pas dans la liste, vous devez démarrer le processus vssphost4.exe traitent dans l'instance de Visual Studio où vous exécutez l'extension.  En général, vous effectuez cette opération en exécutant une action qui permet de connecter Visual Studio au site SharePoint sur l'ordinateur de développement.  Par exemple, Visual Studio démarre vssphost4.exe lorsque vous développez un nœud de connexion de site \(nœud qui affiche une URL de site\) sous le nœud **Connexions SharePoint** dans la fenêtre **Explorateur de serveurs**, ou lorsque vous ajoutez certains éléments de projet SharePoint, tels que des éléments **Instance de liste** ou **Récepteur d'événements**, à un projet SharePoint.  
  
4.  Cliquez sur **Attacher**.  
  
5.  Dans l'instance de Visual Studio en cours de débogage, effectuez les opérations qui sont nécessaires à l'exécution de votre commande.  
  
## Modification des valeurs de Registre pour faciliter le débogage des extensions d'outils SharePoint  
 Lorsque vous déboguez une extension des outils SharePoint dans Visual Studio, vous pouvez modifier des valeurs dans le Registre pour faciliter le dépannage de l'extension.  Les valeurs se trouvent sous la clé HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools.  Ces valeurs n'existent pas par défaut.  
  
 Pour faciliter le dépannage de n'importe quelle extension des outils SharePoint, il vous est possible de créer et définir la valeur EnableDiagnostics.  Le tableau suivant décrit cette valeur.  
  
|Valeur|Description|  
|------------|-----------------|  
|EnableDiagnostics|REG\_DWORD qui spécifie si les messages de diagnostic sont affichés dans la fenêtre **Sortie**.<br /><br /> Pour afficher les messages de diagnostic, remplacez cette valeur par 1.  Pour arrêter l'affichage des messages, définissez cette valeur à 0 ou supprimez\-la.<br /><br /> Pour écrire des messages dans la fenêtre **Sortie** d'une extension d'outils SharePoint, utilisez le service de projet SharePoint.  Pour plus d'informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Si votre extension inclut une commande SharePoint, créez et définissez des valeurs supplémentaires pour faciliter le dépannage de la commande.  Le tableau suivant décrit ces valeurs.  
  
|Valeur|Description|  
|------------|-----------------|  
|AttachDebuggerToHostProcess|REG\_DWORD qui spécifie si une boîte de dialogue permettant d'attacher le débogueur à vssphost4.exe dès son démarrage doit s'afficher.  Ce comportement est utile si la commande que vous souhaitez déboguer est exécutée par vssphost.exe immédiatement après son démarrage et si vous ne disposez pas de suffisamment de temps pour attacher manuellement le débogueur avant l'exécution de la commande.  Pour afficher la boîte de dialogue, vssphost4.exe appelle la méthode <xref:System.Diagnostics.Debugger.Break%2A> lorsqu'il démarre.<br /><br /> Pour activer ce comportement, définissez cette valeur à 1.  Pour désactiver ce comportement, définissez cette valeur à 0 ou supprimez\-la.<br /><br /> Si vous définissez cette valeur à 1, vous pouvez également augmenter la valeur HostProcessStartupTimeout de façon à avoir le temps d'attacher le débogueur avant que vssphost4.exe ne soit censé signaler à Visual Studio qu'il a démarré correctement.|  
|ChannelOperationTimeout|REG\_DWORD qui spécifie la durée, en secondes, pendant laquelle Visual Studio attend qu'une commande SharePoint s'exécute.  Si la commande ne s'exécute pas à l'heure, une <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est 120 secondes.|  
|HostProcessStartupTimeout|REG\_DWORD qui spécifie la durée, en secondes, pendant laquelle Visual Studio attend que vssphost4.exe signale qu'il a démarré.  Si vssphost4.exe ne signale pas de démarrage réussi à l'heure, une <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est 60 secondes.|  
|MaxReceivedMessageSize|REG\_DWORD qui spécifie la taille maximale autorisée, en octets, des messages WCF passés entre Visual Studio et vssphost4.exe.<br /><br /> La valeur par défaut est 1 048 576 octets \(1 Mo\).|  
|MaxStringContentLength|REG\_DWORD qui spécifie la taille maximale autorisée, en octets, des chaînes WCF passées entre Visual Studio et vssphost4.exe.<br /><br /> La valeur par défaut est 1 048 576 octets \(1 Mo\).|  
  
## Voir aussi  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  