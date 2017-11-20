---
title: "Comment : remplir des Documents avec des données à partir des Services | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd71e73d205fb79199cb2b8847a856c97272b066
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Comment : remplir des documents avec les données de services
  Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel et Microsoft Office Word qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d'informations, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L’exemple suivant montre comment ajouter des contrôles liés aux données à des documents au moment du design. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans des Compléments VSTO au moment de l’exécution, consultez [procédure pas à pas : liaison de données à partir d’un Service dans un VSTO complément Project](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour interagir avec les Services Web à partir de Microsoft Excel ?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Pour remplir un projet au niveau du document avec les données d’un service web  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données de service pour votre projet. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).  
  
2.  Faites glisser le tableau ou le champ que vous souhaitez à partir de la fenêtre **Sources de données** vers votre document.  
  
     Un contrôle est créé sur le document, un <xref:System.Windows.Forms.BindingSource> lié à la classe d’objet dans votre projet est créé, et des classes sont générées pour le service.  
  
3.  Dans votre code, créez une instance de la classe de service web à laquelle vous vous êtes connecté à l’étape 1.  
  
4.  Si des propriétés sont nécessaires pour la communication avec le service web, créez des instances de ces propriétés.  
  
5.  Créez et envoyez une demande de données à l’aide des méthodes exposées par le service web et des éventuelles instances de propriétés que vous avez créées à l’étape 4.  
  
     Les méthodes que vous utilisez dépendent de ce que propose le service web.  
  
6.  Affectez la réponse du service web à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> du <xref:System.Windows.Forms.BindingSource>.  
  
 Lorsque vous exécutez le projet, les contrôles affichent le premier enregistrement de la source de données. Vous pouvez activer l’exploration des enregistrements en gérant les événements monétaires à l’aide des objets dans le <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Comment : remplir des feuilles de calcul avec des données à partir d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des Documents avec les données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Guide pratique pour mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  