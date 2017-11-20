---
title: "Comment : remplir des feuilles de calcul avec des données à partir d’une base de données | Documents Microsoft"
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
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b7cfb842a0372d4410a0794ff8ade901af713b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Comment : remplir des feuilles de calcul avec des données provenant d'une base de données
  Vous pouvez accéder des données dans les projets Office au niveau du document de la même façon que vous accédez aux données dans les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel qui ont été améliorés avec des événements et la fonctionnalité de liaison de données. Pour plus d'informations, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans les projets au niveau de l’application en cours d’exécution, consultez [procédure pas à pas : liaison de données complexe dans VSTO complément Project](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire faire : transfert de données dans une feuille de calcul Excel ?](http://go.microsoft.com/fwlink/?LinkID=130277), et [comment faire pour consommer de base de données données dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Ajout d’un contrôle lié aux données à une feuille de calcul au moment du Design  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Pour remplir une feuille de calcul avec des données à partir d’une base de données  
  
1.  Ouvrez un projet de niveau document Excel dans Visual Studio, avec la feuille de calcul ouverte dans le concepteur.  
  
2.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
3.  Faites glisser le champ ou la table que vous souhaitez à partir de la **des Sources de données** fenêtre à votre feuille de calcul.  
  
 Un des contrôles suivants est créé sur la feuille de calcul :  
  
-   Si vous faites glisser un champ, un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle est créé sur la feuille de calcul. Pour plus d’informations, consultez [contrôle NamedRange](../vsto/namedrange-control.md).  
  
-   Si vous faites glisser une table, une <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé sur la feuille de calcul. Pour plus d'informations, consultez [ListObject Control](../vsto/listobject-control.md).  
  
 Vous pouvez ajouter un autre contrôle en sélectionnant la table ou le champ dans le **des Sources de données** fenêtre, puis en choisissant un autre contrôle dans la liste déroulante.  
  
## <a name="objects-in-the-project"></a>Objets du projet  
 Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :  
  
-   Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données. Pour plus d’informations, consultez [outils Dataset dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé. Pour plus d'informations, consultez [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Un TableAdapter qui connecte le dataset typé à la base de données. Pour plus d'informations, consultez [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   Un TableAdapterManager, qui est utilisé pour coordonner des adaptateurs de table dans le jeu de données pour activer les mises à jour hiérarchiques. Pour plus d’informations, consultez [mise à jour hiérarchique](../data-tools/hierarchical-update.md) et [TableAdapterManager référence](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Lorsque vous exécutez le projet, le contrôle affiche le premier enregistrement de la source de données. Vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de faire défiler les enregistrements.  
  
#### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements  
  
-   Utilisez les méthodes <xref:System.Windows.Forms.BindingSource> telles que <xref:System.Windows.Forms.BindingSource.MoveNext%2A> et <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Pour plus d’informations sur l’envoi des mises à jour pour le dataset typé et la base de données, consultez [Comment : mettre à jour une Source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Comment : remplir des Documents avec les données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : remplir des Documents avec des données à partir des Services](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Comment : mettre à jour une Source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Comment faire pour transférer des données dans une feuille de calcul Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Comment faire pour utiliser les données de base de données dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  