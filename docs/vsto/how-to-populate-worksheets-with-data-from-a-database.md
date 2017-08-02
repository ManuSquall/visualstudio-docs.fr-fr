---
title: "Comment&#160;: remplir des feuilles de calcul avec des donn&#233;es provenant d&#39;une base de donn&#233;es"
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
  - "données (développement Office dans Visual Studio), ajouter à des feuilles de calcul"
  - "bases de données (développement Office dans Visual Studio), remplir des feuilles de calcul"
  - "feuilles de calcul (développement Office dans Visual Studio), remplir"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Comment&#160;: remplir des feuilles de calcul avec des donn&#233;es provenant d&#39;une base de donn&#233;es
  Vous pouvez accéder aux données dans Office au niveau de le document projets de la même manière que vous accédez aux données dans les projets Windows Forms.  Vous utilisez les mêmes outils et le même code pour apporter les données dans votre solution et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données.  De plus, vous pouvez tirer parti de contrôles appelés contrôles hôtes. Il s'agit d'objets natifs dans Microsoft Office Excel qui ont été améliorés avec des événements et une fonctionnalité de liaison de données.  Pour plus d’informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 L'exemple suivant indique comment ajouter des contrôles liés aux données dans des projets au niveau du document à l'aide d'un concepteur.  Pour obtenir un exemple d'ajout de contrôles liés aux données dans des projets au niveau de l'application au moment de l'exécution, consultez [Procédure pas à pas : liaison de données complexe dans un projet de complément VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![lien vers la vidéo](~/docs/data-tools/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [Comment faire pour transférer des données dans une feuille de calcul Excel ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=130277) et [Comment faire pour consommer des données de base de données dans Excel ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## Ajout d'un contrôle lié aux données à une feuille de calcul au moment du design  
  
#### Pour remplir une feuille de calcul avec les données d'une base de données  
  
1.  Ouvrez un projet au niveau du document Excel dans Visual Studio, avec la feuille de calcul ouverte dans le concepteur.  
  
2.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet.  Pour plus d’informations, consultez [Comment : établir une connexion à des données d'une base de données](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Faites glisser le champ ou la table de votre choix de la fenêtre **Sources de données** vers votre feuille de calcul.  
  
 L'un des contrôles suivants est créé dans la feuille de calcul :  
  
-   Si vous faites glisser un champ, un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est créé dans la feuille de calcul.  Pour plus d’informations, consultez [NamedRange, contrôle](../vsto/namedrange-control.md).  
  
-   Si vous faites glisser une table, un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> est créé dans la feuille de calcul.  Pour plus d’informations, consultez [ListObject, contrôle](../vsto/listobject-control.md).  
  
 Pour ajouter un autre contrôle, sélectionnez la table ou le champ dans la fenêtre **Sources de données**, puis choisissez un autre contrôle dans la liste déroulante.  
  
## Objets dans le projet  
 Outre le contrôle, les objets liés aux données suivants sont ajoutés automatiquement à votre projet :  
  
-   Un groupe de données typé qui encapsule les tables de données que vous avez liées dans la base de données.  Pour plus d’informations, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au groupe de données typé.  Pour plus d’informations, consultez [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
-   Un TableAdapter qui connecte le groupe de données typé à la base de données.  Pour plus d’informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un TableAdapterManager, utilisé pour coordonner des adaptateurs de table dans le groupe de données pour activer des mises à jour hiérarchiques.  Pour plus d'informations, consultez [Mise à jour hiérarchique](../data-tools/hierarchical-update.md) et [Vue d'ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Lorsque vous exécutez le projet, le contrôle affiche le premier enregistrement dans la source de données.  Vous pouvez utiliser <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de faire défiler les enregistrements.  
  
#### Pour faire défiler les enregistrements  
  
-   Utilisez des méthodes <xref:System.Windows.Forms.BindingSource> telles que <xref:System.Windows.Forms.BindingSource.MoveNext%2A> et <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Pour plus d'informations sur l'envoi de mises à jour au groupe de données typé et à la base de données, consultez [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données de services](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Comment faire : Transférer les données dans une feuille de calcul Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Comment faire : Consommez les données de la base de données dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  