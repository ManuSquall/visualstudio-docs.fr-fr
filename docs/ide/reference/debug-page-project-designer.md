---
title: "Page D&#233;boguer, Concepteur de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "Concepteur de projets, page Déboguer"
  - "page Déboguer dans le Concepteur de projets"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Page D&#233;boguer, Concepteur de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  Cette rubrique ne s'applique pas aux applications de mémoire windows.  Consultez [Démarrer une session de débogage \(VB, C\#, C\+\+ et XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) centre de développement \(dev\) windows.  
  
 Utilisez la page **DéboguerConcepteur de projets** pour définir des propriétés pour déboguer le comportement dans un projet Visual Basic ou C\#.  
  
 Pour accéder à la page **Déboguer** , sélectionnez un nœud de projet dans **Explorateur de solutions**.  Dans le menu **Projet** , choisissez *Nomprojet***Propriétés**.  Lorsque **Concepteur de projets** s'affiche, cliquez sur **Déboguer** tableau.  
  
## Configuration et Plateforme  
 Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou modifier.  
  
 **Configuration**  
 Spécifie les paramètres de configuration à afficher ou à modifier.  Les paramètres peuvent être **Déboguer** \(valeur par défaut\), **Version finale**, ou **Toutes les configurations**.  Pour plus d’informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plateforme**  
 Spécifie les paramètres de plateforme à afficher ou à modifier.  Les tableaux peuvent inclure **Any CPU** \(valeur par défaut\), **x64**, et **x86**.  Pour plus d’informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
## Action de démarrage  
 **Action de démarrage** indique à l'élément de démarrer lorsque l'application est déboguée : le projet, un programme personnalisé, une URL, ou rien.  Par défaut, cette option est définie à **Démarrer le projet**.  **Action de démarrage** Définissant sur la page **Déboguer** détermine la valeur de la propriété d' `StartAction` .  
  
 **Démarrer le projet**  
 Sélectionnez cette option pour spécifier que le fichier exécutable \(pour les projets d'application Windows et d'application console\) doit être démarré lors de le débogage de l'application.  Cette option est activée par défaut.  
  
 **Démarrer le programme externe**  
 Sélectionnez cette option pour spécifier qu'un programme spécifique doit être démarré lors de le débogage de l'application.  
  
 **Démarrer le navigateur avec l'URL**  
 Sélectionnez cette option pour spécifier qu'une URL particulière doit être accessible lorsque l'application est déboguée.  
  
## Options de démarrage  
 **Arguments de la ligne de commande**  
 Dans cette zone de texte, entrez les arguments de ligne de commande à utiliser pour le débogage.  
  
 **Répertoire de travail**  
 Dans cette zone de texte, entrez le répertoire à partir duquel le projet sera lancé.  Ou cliquez sur le bouton Parcourir \(**...**\) pour sélectionner un répertoire.  
  
 **Utiliser l'ordinateur distant**  
 Pour déboguer l'application à partir d'un ordinateur distant, activez cette case à cocher, puis entrez le chemin d'accès à l'ordinateur distant dans la zone de texte.  
  
## Activer les débogueurs  
 **Activer le débogage de code non managé**  
 Cette option spécifie si le débogage de code natif est pris en charge.  Activez cette case à cocher si vous effectuez des appels aux objets COM ou si vous démarrez un programme personnalisé écrit en code natif qui appelle votre projet et vous devez déboguer le code natif.  Désactivez cette case à cocher pour désactiver le débogage de code non managé.  Elle est désactivée par défaut.  
  
 **Activer le débogage SQL Server**  
 Sélectionnez ou désactivez cette case à cocher pour activer ou désactiver le débogage des procédures SQL de votre application Visual Basic.  Elle est désactivée par défaut.  
  
 **Activer le processus d'hébergement Visual Studio**  
 Activez cette case à cocher pour activer le processus d'hébergement Visual Studio.  Elle est activée par défaut.  Pour plus d’informations, consultez [Processus d'hébergement \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md).  
  
 Pour déboguer dans une zone de sécurité, vous devez permettre à ces option et **Déboguez cette application avec le jeu d'autorisations sélectionné** dans [Paramètres de sécurité avancés, boîte de dialogue](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## Voir aussi  
 [Débogage dans Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Paramètres de projet pour des configurations Debug C\#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/fr-fr/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)