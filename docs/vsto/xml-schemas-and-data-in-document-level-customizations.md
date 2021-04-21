---
title: Schémas et données XML dans les personnalisations au niveau du document
description: Microsoft Excel et Word vous permettent de mapper des schémas à vos documents et de simplifier l’importation et l’exportation de données XML dans et hors du document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54e993f41787cfa44bb0aaa78cc7aff8fbad53d8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826588"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schémas et données XML dans les personnalisations au niveau du document
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel et Microsoft Office Word offrent la possibilité de mapper des schémas à vos documents. Cette fonctionnalité permet de simplifier l’importation et l’exportation de données XML dans et hors du document.

 Visual Studio expose les éléments de schéma mappés dans les personnalisations au niveau du document en tant que contrôles dans le modèle de programmation. Pour Excel, Visual Studio ajoute la prise en charge de la liaison des contrôles aux données dans les bases de données, les services Web et les objets. Pour Word et Excel, Visual Studio ajoute la prise en charge des volets actions, qui peuvent être utilisés avec un document mappé à un schéma pour créer une expérience utilisateur final améliorée pour vos solutions. Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

> [!NOTE]
> Vous ne pouvez pas utiliser des schémas XML en plusieurs parties dans les solutions Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objets créés quand des schémas sont attachés à des classeurs Excel
 Lorsque vous attachez un schéma à un classeur, Visual Studio crée automatiquement plusieurs objets et les ajoute à votre projet. Ces objets ne doivent pas être supprimés à l’aide de Visual Studio Tools, car ils sont gérés par Excel. Pour les supprimer, supprimez les éléments mappés de la feuille de calcul ou détachez le schéma à l’aide des outils Excel.

 Il existe deux objets principaux :

- Schéma XML (fichier XSD). Pour chaque schéma du classeur, Visual Studio ajoute un schéma au projet. Il apparaît en tant qu’élément de projet avec une extension XSD dans **Explorateur de solutions**.

- Une classe <xref:System.Data.DataSet> typée. Cette classe est créée en fonction du schéma. Cette classe de DataSet est visible dans **affichage de classes**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objets créés lorsque des éléments de schéma sont mappés à des feuilles de calcul Excel
 Quand vous mappez un élément de schéma du volet Office **source XML** à une feuille de calcul, Visual Studio crée automatiquement plusieurs objets et les ajoute à votre projet :

- Commandes. Pour chaque objet mappé dans le classeur, un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle (pour les éléments de schéma non répétitifs) ou un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle (pour les éléments de schéma répétitifs) est créé dans le modèle de programmation. Le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle peut être supprimé uniquement en supprimant les mappages et les objets mappés du classeur. Pour plus d’informations sur les contrôles, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

- BindingSource. Lorsque vous créez un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> en mappant un élément de schéma non répétitif à la feuille de calcul, <xref:System.Windows.Forms.BindingSource> un est créé et le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle est lié au <xref:System.Windows.Forms.BindingSource> . Vous devez lier le <xref:System.Windows.Forms.BindingSource> à une instance de la source de données qui correspond au schéma mappé au document, tel qu’une instance de la classe typée <xref:System.Data.DataSet> qui a été créée. Créez la liaison en définissant <xref:System.Windows.Forms.BindingSource.DataSource%2A> les <xref:System.Windows.Forms.BindingSource.DataMember%2A> Propriétés et, qui sont exposées dans la fenêtre **Propriétés** .

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>N’est pas créé pour les <xref:Microsoft.Office.Tools.Excel.ListObject> objets. Vous devez lier manuellement le <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données en définissant les <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Propriétés et dans la fenêtre **Propriétés** .

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Schémas Office mappés et fenêtre sources de données Visual Studio
 La fonctionnalité de schéma mappé d’Office et la fenêtre sources de **données** Visual Studio peuvent vous aider à présenter des données dans une feuille de calcul Excel pour la création de rapports ou la modification. Dans les deux cas, vous pouvez faire glisser des éléments de données sur la feuille de calcul Excel. Les deux méthodes créent des contrôles qui sont liés aux données via un <xref:System.Windows.Forms.BindingSource> vers une source de données telle qu’un <xref:System.Data.DataSet> ou un service Web.

> [!NOTE]
> Quand vous mappez un élément de schéma répétitif à une feuille de calcul, Visual Studio crée un <xref:Microsoft.Office.Tools.Excel.ListObject> . Le <xref:Microsoft.Office.Tools.Excel.ListObject> n’est pas lié automatiquement aux données via <xref:System.Windows.Forms.BindingSource> . Vous devez lier manuellement le <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données en définissant les <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> Propriétés et dans la fenêtre **Propriétés** .

 Le tableau suivant présente certaines des différences entre les deux méthodes.

|schéma XML|Fenêtre Sources de données|
|----------------|-------------------------|
|Utilise l’interface Office.|Utilise la fenêtre **sources de données** dans Visual Studio.|
|Active les fonctionnalités Office intégrées pour l’importation et l’exportation de données à partir de fichiers XML.|Vous devez fournir des fonctionnalités d’importation et d’exportation par programmation.|
|Vous devez écrire du code pour remplir les contrôles générés avec des données.|Les contrôles ajoutés à partir de la fenêtre **sources de données** ont du code généré automatiquement pour les remplir, ainsi que les chaînes de connexion nécessaires lorsque vous utilisez des serveurs de base de données.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportement lorsque des schémas sont attachés à des documents Word
 Les objets de données ne sont pas créés lorsque vous attachez un schéma à un document Word qui est utilisé dans un projet Office au niveau du document. Toutefois, lorsque vous mappez un élément de schéma à votre document, des contrôles sont créés. Le type de contrôle dépend du type d’élément que vous mappez ; les éléments répétitifs génèrent <xref:Microsoft.Office.Tools.Word.XMLNodes> des contrôles, et les éléments non répétitifs génèrent des <xref:Microsoft.Office.Tools.Word.XMLNode> contrôles. Pour plus d’informations, consultez [contrôle XMLNodes](../vsto/xmlnodes-control.md) et [contrôle XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Déploiement de solutions incluant des schémas XML
 Vous devez créer un programme d’installation pour déployer une solution qui utilise un schéma XML qui est mappé à un document. Le programme d’installation doit inscrire le schéma dans la bibliothèque de schémas sur l’ordinateur de l’utilisateur. Si vous n’inscrivez pas le schéma, la solution fonctionnera toujours, car Word génère un schéma temporaire basé sur les éléments qui se trouvent dans le document lorsque l’utilisateur l’ouvre. Toutefois, l’utilisateur ne pourra pas effectuer de validation ou enregistrer le schéma utilisé pour créer le projet. Pour plus d’informations sur les programmes d’installation, consultez [déployer des applications, des services et des composants](../deployment/deploying-applications-services-and-components.md).

 Vous pouvez également ajouter du code à votre projet pour vérifier si le schéma est dans la bibliothèque et s’il est enregistré. Si ce n’est pas le cas, vous pouvez avertir l’utilisateur.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>Voir aussi

- [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
