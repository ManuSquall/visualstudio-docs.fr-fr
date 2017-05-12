---
title: "Comment&#160;: personnaliser un package de solution SharePoint &#224; l&#39;aide de cibles de MSBuild"
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
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: personnaliser un package de solution SharePoint &#224; l&#39;aide de cibles de MSBuild
  En spécifiant des cibles de MSBuild sur la ligne de commande, vous pouvez personnaliser le mode de création des fichiers de package SharePoint \(.wsp\) par Visual Studio.  Par exemple, vous pouvez personnaliser les propriétés MSBuild qui modifie le répertoire intermédiaire d'empaquetage et les groupes d'éléments MSBuild qui spécifient les fichiers énumérés.  
  
## Personnalisation et exécution des cibles MSBuild  
 Si vous personnalisez les cibles BeforeLayout et AfterLayout, vous pouvez effectuer les tâches de disposition du package, telles que l'ajout, la suppression, ou la modification des fichiers qui sont dans un package.  
  
#### Pour personnaliser la cible BeforeLayout  
  
1.  Ouvrir un éditeur, tel que le Bloc\-notes, puis ajoutez le code suivant.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Cet exemple affiche un message avant l'empaquetage de cette cible.  
  
2.  Nommez le fichier **CustomLayout.SharePoint.targets**, puis enregistrez\-le dans le dossier du projet SharePoint.  
  
3.  Ouvrez le projet, ouvrez le menu contextuel, puis sélectionnez **Décharger le projet**.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet indisponible et choisissez **Modifier**  *ProjectName***.vbproj** ou **Modifier** *ProjectName***.csproj**.  
  
5.  Après la ligne `Import` vers la fin du fichier de projet, ajoutez la ligne suivante.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Enregistrez et fermez le fichier de projet.  
  
7.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Recharger le projet**.  
  
 Lorsque vous publiez un projet, le message apparaît avant que l'empaquetage ne commence.  
  
#### Pour personnaliser la cible AfterLayout  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Ouvrir**, **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier**, accédez au dossier du projet, sélectionnez le fichier CustomLayout.target, puis cliquez sur le bouton **Ouvrir**.  
  
3.  Juste avant la balise `</Project>`, ajoutez le code ci\-dessous :  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Cet exemple affiche un message après que cette cible soit empaquetée.  
  
4.  Enregistrez et fermez le fichier cible.  
  
5.  Redémarrez Visual Studio puis ouvrez votre projet.  
  
 Lorsque vous publiez un projet, le message de BeforeLayout apparaît avant que l'empaquetage ne commence, et le message d'AfterLayout apparaît une fois la création du package terminée.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  