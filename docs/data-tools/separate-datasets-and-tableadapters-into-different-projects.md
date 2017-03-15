---
title: "Comment&#160;: s&#233;parer les Datasets et les TableAdapters dans diff&#233;rents projets | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "applications multicouches, séparer des DataSets et des TableAdapters"
  - "TableAdapters, applications multicouches"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: s&#233;parer les Datasets et les TableAdapters dans diff&#233;rents projets
Les groupes de données typés ont été améliorés afin que les classes [TableAdapters](../Topic/TableAdapters.md) et DataSet puissent être générées dans des projets séparés.  Cela permet de séparer rapidement les couches Application et de générer des applications de données multicouches.  
  
 La procédure suivante explique comment utiliser le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md) pour générer le code du groupe de données dans un projet qui est séparé du projet qui contient le code du `TableAdapter` généré.  
  
## Séparation des DataSets et des TableAdapters  
 Lorsque vous séparez le code du groupe de données du code du `TableAdapter`, le projet qui contient le code du groupe de données doit se trouver dans la solution actuelle.  Si ce projet ne se trouve pas dans la solution actuelle, il ne sera pas disponible dans la liste **Projet DataSet** dans la fenêtre **Propriétés**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour séparer le groupe de données dans un projet différent  
  
1.  Ouvrez une solution qui contient un groupe de données \(fichier .xsd\).  
  
    > [!NOTE]
    >  Si la solution ne contient pas le projet dans lequel vous souhaitez séparer le code du groupe de données, créez\-le ou ajoutez un projet existant à la solution.  
  
2.  Ouvrez le groupe de données dans le **Concepteur de DataSet** en double\-cliquant sur le fichier de groupe de données typé \(un fichier .xsd\) dans l'**Explorateur de solutions**.  
  
3.  Cliquez sur une zone vide du **Concepteur de DataSet**.  
  
4.  Localisez le nœud **Projet DataSet** dans la fenêtre **Propriétés**.  
  
5.  Dans la liste **Projet DataSet**, cliquez sur le nom du projet dans lequel vous souhaitez générer le code du groupe de données.  
  
     Après avoir cliqué sur le projet dans lequel vous souhaitez générer le code du groupe de données, la propriété **Fichier de groupe de données** est remplie avec un nom de fichier par défaut.  Vous pouvez modifier ce nom si nécessaire.  En outre, si vous souhaitez générer le code du groupe de données dans un répertoire spécifique, vous pouvez affecter le nom d'un dossier à la propriété **Dossier du projet**.  
  
    > [!NOTE]
    >  Lorsque vous séparez des groupes de données et des TableAdapters \(en définissant la propriété **Projet DataSet**\), les classes DataSet partielles existant dans le projet ne sont pas automatiquement déplacées.  En effet, ces classes doivent être déplacées manuellement vers le projet DataSet.  
  
6.  Enregistrez le groupe de données.  
  
     Le code du groupe de données est généré dans le projet sélectionné dans la propriété **Projet DataSet**  et le code du **TableAdapter** est généré dans le projet actuel.  
  
 Par défaut, une fois que vous avez séparé le code du groupe de données et le code du `TableAdapter`, vous obtenez un fichier de classe discret dans chaque projet.  Le projet d'origine a un fichier nommé NomGroupeDonnées.Designer.vb \(ou NomGroupeDonnées.Designer.cs\) qui contient le code du `TableAdapter`.  Le projet désigné dans la propriété **Projet DataSet** a un fichier nommé NomGroupeDonnées.DataSet.Designer.vb \(ou NomGroupeDonnées.DataSet.Designer.cs\) qui contient le code du groupe de données.  
  
> [!NOTE]
>  Sélectionnez le projet du groupe de données ou du `TableAdapter` et cliquez sur **Afficher tous les fichiers** dans l'**Explorateur de solutions** pour consulter le fichier de classe généré.  
  
## Voir aussi  
 [Vue d'ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Procédure pas à pas : création d'une application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)