---
title: "Comment&#160;: cr&#233;er un package de solution SharePoint &#224; l&#39;aide de t&#226;ches MSBuild"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, packages"
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er un package de solution SharePoint &#224; l&#39;aide de t&#226;ches MSBuild
  Vous pouvez générer, nettoyer et valider un package SharePoint \(.wsp\) en exécutant des tâches MSBuild de ligne de commande sur un ordinateur de développement.  Il est possible, en outre, d'utiliser ces commandes pour automatiser le processus de génération en tirant parti de l'outil Team Foundation Server sur un ordinateur de build.  
  
## Génération d'un package SharePoint  
  
#### Pour générer un package SharePoint  
  
1.  Dans le menu Windows**Démarrer**, choisissez **Tous les programmes**, **Accessoires**, **Invite de commandes**.  
  
2.  Modifiez le répertoire dans lequel votre projet SharePoint est enregistré.  
  
3.  Entrez la commande suivante pour créer un package pour le projet.  Remplacez *ProjectFileName* par le nom du projet.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l'une des commandes suivantes pour empaqueter un projet SharePoint appelé ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## Nettoyage d'un package SharePoint  
  
#### Pour nettoyer un package SharePoint  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Modifiez le répertoire dans lequel votre projet SharePoint est enregistré.  
  
3.  Entrez la commande suivante pour nettoyer un package pour le projet.  Remplacez *ProjectFileName* par le nom du projet.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l'une des commandes suivantes pour nettoyer un projet SharePoint appelé ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## Validation d'un package SharePoint  
  
#### Pour valider un package SharePoint  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Modifiez le répertoire dans lequel votre projet SharePoint est enregistré.  
  
3.  Entrez la commande suivante pour valider un package pour le projet.  Remplacez *ProjectFileName* par le nom du projet.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l'une des commandes suivantes pour valider un projet SharePoint appelé ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## Définition des propriétés dans un package SharePoint  
  
#### Pour définir une propriété dans un package SharePoint  
  
1.  Ouvrez une fenêtre d'invite de commandes.  
  
2.  Modifiez le répertoire dans lequel votre projet SharePoint est enregistré.  
  
3.  Entrez la commande suivante pour définir une propriété dans un package pour le projet.  Remplacez *PropertyName* par la propriété qui vous intéresse.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Vous pourriez, par exemple, exécuter la commande suivante pour définir le niveau d'avertissement.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## Voir aussi  
 [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  