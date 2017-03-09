---
title: "Liaison de contr&#244;les &#224; des donn&#233;es dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Sources de données (fenêtre)"
  - "sources de données, afficher les données"
  - "données, afficher"
  - "afficher les données"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Liaison de contr&#244;les &#224; des donn&#233;es dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles.  Vous pouvez créer ces contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données** sur une aire de conception dans Visual Studio.  
  
 Cette rubrique décrit les sources de données que vous pouvez utiliser pour créer des contrôles liés aux données.  Elle décrit également certaines des tâches générales qui entrent en jeu dans la liaison de données.  Pour des informations plus détaillées sur la création de contrôles liés aux données, consultez [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md), [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) et [Liaison de contrôles Silverlight avec des données dans Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md).  
  
## Sources de données  
 Une source de données représente les données qui sont disponibles pour votre application.  Vous pouvez créer des sources de données à partir de bases de données, de services ou d'objets.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md).  
  
 Certaines sources de données vous permettent de créer des contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données**, contrairement à d'autres sources de données.  Le tableau suivant affiche les sources de données qui sont prises en charge.  
  
|Source de données|Prise en charge du glisser\-déplacer dans le **Concepteur Windows Forms**|Prise en charge du glisser\-déplacer dans le **Concepteur WPF**|Prise en charge du glisser\-déplacer dans le **Concepteur Silverlight**|  
|-----------------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------------------------|  
|Groupe de données|Oui|Oui|Non|  
|Entity Data Model|Non<sup>1</sup>|Oui|Oui|  
|Classes LINQ to SQL|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|Services \(notamment [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], les services WCF et les services Web\)|Oui|Oui|Oui|  
|Objet|Oui|Oui|Oui|  
|SharePoint|Oui|Oui|Oui|  
  
 1.  Lorsque le **Concepteur Windows Forms** est ouvert, les entités figurant dans la fenêtre **Sources de données** sont en lecture seule et ne peuvent pas être déplacées vers le concepteur.  Toutefois, vous pouvez toujours créer des contrôles liés aux données en ajoutant une nouvelle source de données Objet basée sur l'Entity Data Model, puis faire glisser ces objets vers le concepteur.  
  
 2.  Les classes LINQ to SQL ne s'affichent pas dans la fenêtre **Sources de données**.  Toutefois, vous pouvez ajouter une nouvelle source de données Objet basée sur les classes LINQ to SQL, puis faire glisser ces objets vers le concepteur pour créer des contrôles liés aux données.  Pour plus d'informations, consultez [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
## Fenêtre Sources de données  
 Les sources de données peuvent être utilisées par votre projet sous la forme d'éléments dans la fenêtre **Sources de données**.  Vous pouvez faire glisser des éléments à partir de cette fenêtre pour créer des contrôles liés aux données sous\-jacentes.  Pour plus d'informations, consultez [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
 Pour chaque type de données qui apparaît dans la fenêtre **Sources de données**, un contrôle par défaut est créé lorsque vous faites glisser l'élément vers le concepteur.  Avant de faire glisser un élément de la fenêtre **Sources de données**, vous pouvez modifier le contrôle qui sera créé.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Tâches impliquées dans la liaison de contrôles à des données  
 Le tableau suivant répertorie certaines des tâches les plus courantes effectuées pour lier des contrôles à des données.  
  
|Tâche|Complément d'information|  
|-----------|------------------------------|  
|Ouvrez la fenêtre **Sources de données**|[Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md)|  
|Ajoutez une source de données à votre projet|[Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [Comment : se connecter à des données dans un service](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|Définir le contrôle créé lorsque vous faites glisser un élément de la fenêtre **Sources de données** vers le concepteur.|[Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modifier la liste des contrôles associés aux éléments dans la fenêtre **Sources de données**.|[Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Créer des contrôles liés aux données.|[Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [Liaison de contrôles Silverlight avec des données dans Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 Après avoir créé des contrôles liés aux données, vous pouvez effectuer l'une des tâches suivantes.  
  
|Tâche|Pour plus d'informations|  
|-----------|------------------------------|  
|Modifier les données contenues dans la source de données sous\-jacente|[Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)|  
|Valider les modifications apportées aux données|[Validation des données](../Topic/Validating%20Data.md)|  
|Enregistrer les données mises à jour dans la base de données|[Enregistrement des données](../data-tools/saving-data.md)|  
  
## Voir aussi  
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Liaison de contrôles Silverlight avec des données dans Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [Comment : lier des contrôles à des images d'une base de données](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Outils permettant d'utiliser des sources de données dans Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)