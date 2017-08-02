---
title: "Comment&#160;: remplir des documents avec les donn&#233;es de services"
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
  - "documents (développement Office dans Visual Studio), remplissage à l’aide de données"
  - "services web (développement Office dans Visual Studio), remplissage de documents"
  - "données (développement Office dans Visual Studio), ajout à des documents"
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Comment&#160;: remplir des documents avec les donn&#233;es de services
  Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel et Microsoft Office Word qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L’exemple suivant montre comment ajouter des contrôles liés aux données à des documents au moment du design. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans des compléments VSTO au moment de l’exécution, consultez [Procédure pas à pas : Liaison à des données de service dans un projet de complément VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![lien vers la vidéo](~/data-tools/media/playvideo.gif "lien vers la vidéo") Pour obtenir une démonstration vidéo connexe, consultez [Comment faire pour interagir avec ses services web à partir de Microsoft Excel ?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### Pour remplir un projet au niveau du document avec les données d’un service web  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données de service pour votre projet. Pour plus d'informations, consultez [Comment : se connecter à des données dans un service](~/data-tools/how-to-connect-to-data-in-a-service.md).  
  
2.  Faites glisser le tableau ou le champ que vous souhaitez à partir de la fenêtre **Sources de données** vers votre document.  
  
     Un contrôle est créé sur le document, un <xref:System.Windows.Forms.BindingSource> lié à la classe d’objet dans votre projet est créé, et des classes sont générées pour le service.  
  
3.  Dans votre code, créez une instance de la classe de service web à laquelle vous vous êtes connecté à l’étape 1.  
  
4.  Si des propriétés sont nécessaires pour la communication avec le service web, créez des instances de ces propriétés.  
  
5.  Créez et envoyez une demande de données à l’aide des méthodes exposées par le service web et des éventuelles instances de propriétés que vous avez créées à l’étape 4.  
  
     Les méthodes que vous utilisez dépendent de ce que propose le service web.  
  
6.  Affectez la réponse du service web à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> du <xref:System.Windows.Forms.BindingSource>.  
  
 Lorsque vous exécutez le projet, les contrôles affichent le premier enregistrement de la source de données. Vous pouvez activer l’exploration des enregistrements en gérant les événements monétaires à l’aide des objets dans le <xref:System.Windows.Forms.BindingSource>.  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Comment : remplir des feuilles de calcul avec des données provenant d'une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  