---
title: "Comment&#160;: mettre &#224; jour une source de donn&#233;es avec les donn&#233;es d&#39;un contr&#244;le h&#244;te"
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
  - "documents (développement Office dans Visual Studio), mises à jour de source de données"
  - "données (développement Office dans Visual Studio), mise à jour d’une source de données à partir d’un document"
  - "contrôles hôtes (développement Office dans Visual Studio), mises à jour de source de données"
  - "documents Office (développement Office dans Visual Studio), sources de données"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Comment&#160;: mettre &#224; jour une source de donn&#233;es avec les donn&#233;es d&#39;un contr&#244;le h&#244;te
  Vous pouvez lier un contrôle hôte à une source de données et mettre à jour la source de données avec les modifications apportées aux données dans le contrôle. Deux étapes principales constituent ce processus :  
  
1.  Mise à jour de la source de données en mémoire avec les données modifiées dans le contrôle. En général, la source de données en mémoire est un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable> ou un objet de données.  
  
2.  Mise à jour de la base de données avec les données modifiées dans la source de données en mémoire. Ceci s’applique uniquement si la source de données est connectée à une base de données principale, par exemple une base de données SQL Server ou Microsoft Office Access.  
  
 Pour plus d’informations sur la liaison de données et les contrôles hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Mise à jour de la source de données en mémoire  
 Par défaut, les contrôles hôtes qui autorisent la liaison de données simple \(comme les contrôles de contenu dans un document Word ou un contrôle de plage nommée dans une feuille de calcul Excel\) n’enregistrent pas les modifications de données apportées à la source de données en mémoire. Autrement dit, quand un utilisateur final modifie une valeur dans un contrôle hôte, puis quitte le contrôle, la nouvelle valeur du contrôle n’est pas enregistrée automatiquement dans la source de données.  
  
 Pour enregistrer les données dans la source de données, vous pouvez écrire du code qui met à jour la source de données en réponse à un événement spécifique au moment de l’exécution, ou vous pouvez configurer le contrôle pour mettre à jour la source de données automatiquement quand la valeur du contrôle change.  
  
 Vous n’avez pas besoin d’enregistrer les modifications <xref:Microsoft.Office.Tools.Excel.ListObject> apportées à la source de données en mémoire. Quand vous liez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> à des données, le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> enregistre automatiquement les modifications dans la source de données en mémoire sans que du code supplémentaire soit nécessaire.  
  
#### Pour mettre à jour la source de données en mémoire au moment de l’exécution  
  
-   Appelez la méthode <xref:System.Windows.Forms.Binding.WriteValue%2A> de l’objet <xref:System.Windows.Forms.Binding> qui lie le contrôle à la source de données.  
  
     L’exemple suivant enregistre dans la source de données les modifications apportées à un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans une feuille de calcul Excel. Cet exemple part du principe que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `namedRange1`, dont la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> est liée à un champ dans une source de données.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### Mise à jour automatique de la source de données en mémoire  
 Vous pouvez également configurer un contrôle pour qu’il mette automatiquement à jour la source de données en mémoire. Dans un projet au niveau du document, vous pouvez pour cela utiliser du code ou le concepteur. Dans un projet de complément VSTO, vous devez utiliser du code.  
  
##### Pour configurer un contrôle pour qu’il mette automatiquement à jour la source de données en mémoire à l’aide de code  
  
1.  Utilisez le mode System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  de l’objet <xref:System.Windows.Forms.Binding> qui lie le contrôle à la source de données. Il existe deux options de mise à jour de la source de données :  
  
    -   Pour mettre à jour la source de données quand le contrôle est validé, affectez la valeur System.Windows.Forms.DataSourceUpdateMode.OnValidation à cette propriété.  
  
    -   Pour mettre à jour la source de données quand la valeur de la propriété liée aux données du contrôle change, affectez la valeur System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged à cette propriété.  
  
        > [!NOTE]  
        >  L’option System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged ne s’applique pas aux contrôles hôtes Word, car Word n’offre pas de notifications de modification du document ou du contrôle. Toutefois, vous pouvez utiliser cette option pour les contrôles Windows Forms sur les documents Word.  
  
     L’exemple suivant configure un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> pour mettre automatiquement à jour la source de données quand la valeur du contrôle change. Cet exemple part du principe que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `namedRange1`, dont la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> est liée à un champ dans une source de données.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### Pour configurer un contrôle pour qu’il mette automatiquement à jour la source de données en mémoire à l’aide du concepteur  
  
1.  Dans Visual Studio, ouvrez le document Word ou le classeur Excel dans le concepteur.  
  
2.  Cliquez sur le contrôle qui doit mettre à jour la source de données automatiquement.  
  
3.  Dans la fenêtre **Propriétés**, développez la propriété **\(DataBindings\)**.  
  
4.  À côté de la propriété **\(Advanced\)**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "Capture d'écran VisualStudioEllipsesButton")\).  
  
5.  Dans la boîte de dialogue **Mise en forme et liaison avancée**, cliquez sur la liste déroulante **Mode de mise à jour de la source de données** et sélectionnez l’une des valeurs suivantes :  
  
    -   Pour mettre à jour la source de données quand le contrôle est validé, sélectionnez **OnValidation**.  
  
    -   Pour mettre à jour la source de données quand la valeur de la propriété liée aux données du contrôle change, sélectionnez **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  L’option **OnPropertyChanged** ne s’applique pas aux contrôles hôtes Word, car Word n’offre pas de notifications de modification du document ou du contrôle. Toutefois, vous pouvez utiliser cette option pour les contrôles Windows Forms sur les documents Word.  
  
6.  Fermez la boîte de dialogue **Mise en forme et liaison avancée**.  
  
## Mise à jour de la base de données  
 Si la source de données en mémoire est associée à une base de données, vous devez mettre celle\-ci à jour avec les modifications apportées à la source de données. Pour plus d’informations sur la mise à jour d’une base de données, consultez [Enregistrement de données dans des groupes de données](../Topic/Saving%20data%20back%20to%20the%20database.md) et [Comment : mettre à jour les données à l'aide d'un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
#### Pour mettre à jour la base de données  
  
1.  Appelez la méthode <xref:System.Windows.Forms.BindingSource.EndEdit%2A> du <xref:System.Windows.Forms.BindingSource> pour le contrôle.  
  
     Le <xref:System.Windows.Forms.BindingSource> est généré automatiquement quand vous ajoutez un contrôle lié aux données à un document ou à un classeur au moment du design. Le <xref:System.Windows.Forms.BindingSource> connecte le contrôle au dataset typé dans votre projet. Pour plus d'informations, consultez [Vue d'ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
     L’exemple de code suivant part du principe que votre projet contient un <xref:System.Windows.Forms.BindingSource> nommé `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  Appelez la méthode `Update` du TableAdapter généré dans votre projet.  
  
     Le TableAdapter est généré automatiquement quand vous ajoutez un contrôle lié aux données à un document ou à un classeur au moment du design. Le TableAdapter connecte le dataset typé dans votre projet à la base de données. Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     L’exemple de code suivant part du principe que vous avez une connexion à la table Customers dans la base de données Northwind, et que votre projet contient un TableAdapter nommé `customersTableAdapter` et un dataset typé nommé `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Enregistrement de données dans des groupes de données](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Comment : mettre à jour les données à l'aide d'un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Comment : parcourir les enregistrements de base de données dans une feuille de calcul](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Comment : remplir des feuilles de calcul avec des données provenant d'une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données d'objets](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : remplir des documents avec les données de services](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  