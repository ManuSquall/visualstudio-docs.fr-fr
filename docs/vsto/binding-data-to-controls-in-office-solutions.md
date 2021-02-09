---
title: Lier des données à des contrôles dans les solutions Office
description: Découvrez comment vous pouvez lier Windows Forms contrôles et les contrôles hôtes d’un document Word Microsoft Office ou d’une feuille de calcul Excel à une source de données.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 459c50b5f8135756f85de852a62de44b3878148d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882477"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Lier des données à des contrôles dans les solutions Office
  Vous pouvez lier des contrôles Windows Forms et des *contrôles hôtes* dans un document Microsoft Office Word ou une feuille de calcul Microsoft Office Excel à une source de données pour que les contrôles affichent automatiquement les données. Vous pouvez lier des données à des contrôles dans des projets de niveau application et au niveau du document.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Les contrôles hôtes étendent des objets qui se trouvent dans les modèles objet Word et Excel, tels que les contrôles de contenu dans Word et les plages nommées dans Excel. Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

 Les contrôles Windows Forms et les contrôles hôtes utilisent le modèle de liaison de données Windows Forms, qui prend en charge la *liaison de données simple* et la *liaison de données complexe* à des sources de données telles que les datasets et les tables de données. Pour obtenir des informations complètes sur le modèle de liaison de données dans Windows Forms, consultez [liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Liaison de données simple
 Il existe une liaison de données simple quand une propriété de contrôle est liée à un seul élément de données, tel qu’une valeur dans une table de données. Par exemple, le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> a une propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> qui peut être liée à un champ dans un dataset. Lorsque le champ dans le dataset change, la valeur dans la plage nommée change également. Tous les contrôles hôtes, à l’exception du contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> , prennent en charge la liaison de données simple. Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> étant une collection, il ne prend pas en charge la liaison de données.

 Pour effectuer une liaison de données simple à un contrôle hôte, ajoutez un <xref:System.Windows.Forms.Binding> à la propriété `DataBindings` du contrôle. Un objet <xref:System.Windows.Forms.Binding> représente la liaison simple entre une valeur de propriété du contrôle et la valeur d’un élément de données.

 L’exemple suivant montre comment lier la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> à un élément de données dans un projet au niveau du document.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Pour obtenir des procédures pas à pas qui illustrent la liaison de données simple, consultez [procédure pas à pas : liaison de données simple dans un projet au niveau du document](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) pour un projet au niveau du document et [procédure pas à pas : liaison de données simple dans](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) un projet de complément VSTO pour un projet de complément VSTO.

## <a name="complex-data-binding"></a>Liaison de données complexe
 Il existe une liaison de données complexe quand une propriété de contrôle est liée à plusieurs éléments de données, par exemple plusieurs colonnes dans une table de données. Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> pour Excel est le seul contrôle hôte qui prend en charge la liaison de données complexe. Il existe également de nombreux contrôles Windows Forms qui prennent en charge la liaison de données complexe, tels que le contrôle <xref:System.Windows.Forms.DataGridView> .

 Pour effectuer une liaison de données complexe, affectez comme valeur de la propriété `DataSource` du contrôle un objet de source de données qui est pris en charge par la liaison de données complexe. Par exemple, la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être liée à plusieurs colonnes dans une table de données. Toutes les données de la table s’affichent dans le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> , et le <xref:Microsoft.Office.Tools.Excel.ListObject> change à mesure que les données de la table de données changent. Pour obtenir la liste des sources de données que vous pouvez utiliser pour la liaison de données complexe, consultez [sources de données prises en charge par Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 L’exemple de code suivant crée un <xref:System.Data.DataSet> avec deux objets <xref:System.Data.DataTable> et remplit l’une des tables avec des données. Le code lie ensuite le <xref:Microsoft.Office.Tools.Excel.ListObject> à la table qui contient des données. Cet exemple concerne un projet Excel au niveau du document.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Pour obtenir des procédures pas à pas qui illustrent la liaison de données complexe, consultez [procédure pas à pas : liaison de données complexe dans un projet au niveau du document](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) pour un projet au niveau du document et [procédure pas à pas : liaison de données complexe dans](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) un projet de complément VSTO pour un projet de complément VSTO.

## <a name="display-data-in-documents-and-workbooks"></a>Afficher des données dans des documents et des classeurs
 Dans les projets au niveau du document, vous pouvez utiliser la fenêtre **Sources de données** pour ajouter facilement des contrôles liés aux données à vos documents ou vos classeurs, comme vous le feriez pour des Windows Forms. Pour plus d’informations sur l’utilisation de la fenêtre **sources de données** , consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) et [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Faire glisser des contrôles à partir de la fenêtre sources de données
 Un contrôle est créé sur le document quand vous faites glisser un objet sur à partir de la fenêtre **Sources de données** . Le type de contrôle créé varie selon que vous liez une ou plusieurs colonnes de données.

 Pour Excel, un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est créé sur la feuille de calcul pour chaque champ, et un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> est créé pour chaque plage de données qui comprend plusieurs lignes et colonnes. Vous pouvez modifier ce comportement par défaut en sélectionnant la table ou le champ dans la fenêtre **Sources de données** , puis en choisissant un autre contrôle dans la liste déroulante.

 Un contrôle <xref:Microsoft.Office.Tools.Word.ContentControl> est ajouté aux documents. Le type de contrôle de contenu dépend du type de données du champ sélectionné.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Lier des données dans des projets au niveau du document au moment du design
 Les rubriques suivantes présentent des exemples de liaison de données au moment du design :

- [Comment : remplir des feuilles de calcul avec des données d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Comment : remplir des documents avec des données de services](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Comment : faire défiler des enregistrements de base de données dans une feuille de calcul](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Lier des données dans des projets de complément VSTO
 Dans les projets de complément VSTO, vous pouvez ajouter des contrôles uniquement au moment de l’exécution. Les rubriques suivantes présentent des exemples de liaison de données au moment de l’exécution :

- [Procédure pas à pas : liaison de données simple dans un projet de complément VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Procédure pas à pas : liaison de données complexe dans un projet de complément VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Mettre à jour les données liées aux contrôles hôtes
 La liaison de données entre une source de données et un contrôle hôte implique une mise à jour de données bidirectionnelle. Avec la liaison de données simple, les modifications de la source de données sont répercutées automatiquement dans le contrôle hôte, mais les modifications du contrôle hôte nécessitent un appel explicite pour mettre à jour la source de données. En effet, dans certains cas les modifications d’un champ lié aux données ne sont acceptées que si elles sont accompagnées de modifications dans un autre champ lié aux données. Par exemple, vous pouvez avoir deux champs, un pour l’âge et un autre pour les années d’expérience. L’expérience ne peut pas dépasser l’âge. Un utilisateur ne peut pas mettre à jour l’âge de 50 à 25 puis l’expérience de 30 à 10 à moins d’apporter les modifications en même temps. Pour résoudre ce problème, les champs avec liaison de données simple ne sont mis à jour qu’une fois que les mises à jour ont été envoyées explicitement par le code.

 Pour mettre à jour une source de données à partir de contrôles hôtes qui autorisent la liaison de données simple, vous devez envoyer des mises à jour à la source de données en mémoire (comme un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>) et à la base de données principale, si votre solution en utilise une.

 Vous n’avez pas besoin de mettre à jour la source de données en mémoire de manière explicite quand vous effectuez une liaison de données complexe à l’aide du contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> . Dans ce cas, les modifications sont envoyées automatiquement à la source de données en mémoire sans code supplémentaire.

 Pour plus d’informations, consultez [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Voir aussi
- [Liaison de données et Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Comment : créer un contrôle à liaison simple dans un Windows Form](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
- [Mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Données de cache](../vsto/caching-data.md)
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
