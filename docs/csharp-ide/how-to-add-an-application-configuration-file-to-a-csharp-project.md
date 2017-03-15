---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En ajoutant un fichier de configuration de l'application \(fichier app.config\) à un projet en c, vous pouvez personnaliser la façon dont le common langage runtime localise et charge les fichiers d'assembly.  Pour plus d'informations sur les fichiers de configuration de l'application, consultez [Méthode de localisation des assemblys par le runtime](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  La mémoire windows ne prend pas en charge <xref:System.Configuration>.  Par conséquent, les applications de mémoire ne contiennent pas de modèle app.config.  
  
 Lorsque vous générez votre projet, l'environnement de développement copie automatiquement votre fichier app.config, modifie le nom de fichier de la copie pour correspondre à votre fichier exécutable, puis déplace la copie dans le dossier bin.  
  
### Pour ajouter un fichier de configuration de l'application à votre projet C\#  
  
1.  Dans la barre de menus, sélectionnez **Projet**, **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
2.  Développez **Installé**, développez **Éléments Visual C\#**, puis choisissez le modèle **Fichier de configuration de l'application** .  
  
3.  Dans la zone de texte **Nom**, entrez un nom, puis choisissez le bouton **Ajouter** .  
  
     Un fichier nommé app.config est ajouté à votre projet.  
  
## Voir aussi  
 [Gestion des paramètres d'une application \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Schéma des fichiers de configuration](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Configuration d'applications](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/fr-fr/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)