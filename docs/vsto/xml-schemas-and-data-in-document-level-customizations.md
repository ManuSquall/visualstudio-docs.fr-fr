---
title: "Schémas XML et les données dans les personnalisations au niveau du Document | Documents Microsoft"
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
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d53a17484a350e361459f5c975ed3090779332bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schémas et données XML dans les personnalisations au niveau du document
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présenté exclusivement pour le bénéfice et l’utilisation des personnes et des organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui sont à l’aide d’ou de développement programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft avant de janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liées à XML personnalisées à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas lire ou utilisées par des individus ou organisations États-Unis ou dans ses territoires qui utilisent, ou développent des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et une licence d’utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel et Microsoft Office Word permettent de mapper des schémas à vos documents. Cette fonctionnalité peut simplifier l’importation et exportation de données XML vers et à partir du document.  
  
 Visual Studio expose mappé les éléments de schéma dans les personnalisations au niveau du document sous forme de contrôles dans le modèle de programmation. Pour Excel, Visual Studio ajoute la prise en charge de la liaison des contrôles aux données dans les bases de données, les services Web et les objets. Pour Word et Excel, Visual Studio ajoute la prise en charge des volets actions, ce qui peut être utilisé avec un document de schéma mappé pour créer une expérience utilisateur final améliorée pour vos solutions. Pour plus d'informations, consultez [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser les schémas XML en plusieurs parties dans les solutions Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objets créés lorsque les schémas sont joints aux classeurs Excel  
 Lorsque vous attachez un schéma à un classeur, Visual Studio crée plusieurs objets automatiquement et les ajoute à votre projet. Ces objets ne doivent pas être supprimés à l’aide des outils de Visual Studio, car ils sont gérés par Excel. Pour les supprimer, supprimez les éléments mappés de la feuille de calcul ou détachez le schéma à l’aide des outils Excel.  
  
 Il existe deux principaux objets :  
  
-   Schéma XML (fichier XSD). Pour chaque schéma dans le classeur, Visual Studio ajoute un schéma au projet. Il peut s’agit d’un élément de projet avec une extension XSD dans **l’Explorateur de solutions**.  
  
-   Une classe <xref:System.Data.DataSet> typée. Cette classe est créée en fonction du schéma. Cette classe dataset est visible dans **affichage de classes**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objets créés lorsque les éléments de schéma sont mappés aux feuilles de calcul Excel  
 Lorsque vous mappez un élément de schéma à partir de la **Source XML** volet de tâches à une feuille de calcul, Visual Studio crée plusieurs objets automatiquement et les ajoute à votre projet :  
  
-   Contrôles. Pour chaque objet mappé dans le classeur, un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle (pour les éléments de schéma non répétitif) ou un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle (pour la répétition des éléments de schéma) est créé dans le modèle de programmation. Le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle peut être supprimé uniquement en supprimant les mappages et les objets mappés du classeur. Pour plus d’informations sur les contrôles, consultez [des éléments hôtes et vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Lorsque vous créez un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> en mappant un élément de schéma non répétitif à la feuille de calcul, un <xref:System.Windows.Forms.BindingSource> est créé et le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle est lié à la <xref:System.Windows.Forms.BindingSource>. Vous devez lier le <xref:System.Windows.Forms.BindingSource> à une instance de la source de données qui correspond au schéma mappé au document, telles qu’une instance de typées <xref:System.Data.DataSet> classe qui a été créé. Créer la liaison en définissant le <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriétés qui sont exposées dans le **propriétés** fenêtre.  
  
    > [!NOTE]  
    >  Le <xref:System.Windows.Forms.BindingSource> n’est pas créé pour <xref:Microsoft.Office.Tools.Excel.ListObject> objets. Vous devez lier manuellement les <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données en définissant le <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriétés dans le **propriétés** fenêtre.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Schémas mappés Office et la fenêtre Sources de données Visual Studio  
 Les deux fonctionnalités de schéma mappé d’Office et de Visual Studio **des Sources de données** fenêtre peut vous aider à présenter des données sur une feuille de calcul Excel pour la création de rapports ou de modification. Dans les deux cas vous pouvez faire glisser des éléments de données sur la feuille de calcul Excel. Les deux méthodes créent des contrôles qui sont liés aux données via un <xref:System.Windows.Forms.BindingSource> à une source de données comme un <xref:System.Data.DataSet> ou un service Web.  
  
> [!NOTE]  
>  Lorsque vous mappez un élément de schéma répétitif à une feuille de calcul, Visual Studio crée un <xref:Microsoft.Office.Tools.Excel.ListObject>. Le <xref:Microsoft.Office.Tools.Excel.ListObject> n’est pas lié automatiquement aux données via le <xref:System.Windows.Forms.BindingSource>. Vous devez lier manuellement les <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données en définissant le <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriétés dans le **propriétés** fenêtre.  
  
 Le tableau suivant répertorie certaines des différences entre les deux méthodes.  
  
|Schéma XML|Fenêtre Sources de données|  
|----------------|-------------------------|  
|Utilise l’interface Office.|Utilise **des Sources de données** fenêtre dans Visual Studio.|  
|Active les fonctionnalités Office intégrées pour importer et exporter des données à partir de fichiers XML.|Vous devez assurer l’importation et l’exportation par programme.|  
|Vous devez écrire du code pour remplir les contrôles générés avec des données.|Les contrôles ajoutés à partir de la **des Sources de données** fenêtre ont le code généré automatiquement pour les remplir, ainsi que les chaînes de connexion nécessaires lorsque vous utilisez des serveurs de base de données.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportement lorsque les schémas sont joints à des Documents Word  
 Objets de données ne sont pas créés lorsque vous attachez un schéma à un document Word qui est utilisé dans un projet de Office au niveau du document. Toutefois, lorsque vous mappez un élément de schéma à votre document, les contrôles sont créés. Le type de contrôle dépend du type d’élément que vous mappez ; répétition de génèrent des éléments <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles et générer des éléments non répétés <xref:Microsoft.Office.Tools.Word.XMLNode> contrôles. Pour plus d’informations, consultez [contrôle XMLNodes](../vsto/xmlnodes-control.md) et [contrôle XMLNode](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Déploiement de Solutions qui incluent des schémas XML  
 Vous devez créer un programme d’installation pour déployer une solution qui utilise un schéma XML qui est mappé à un document. Le programme d’installation doit enregistrer le schéma dans la bibliothèque de schémas sur l’ordinateur de l’utilisateur. Si vous n’enregistrez pas le schéma, la solution continueront de fonctionner, car Word génère un schéma temporaire basé sur les éléments qui se trouvent dans le document lorsque l’utilisateur l’ouvre. Toutefois, l’utilisateur ne sera pas en mesure d’effectuer la validation ou enregistrer le schéma qui a été utilisé pour créer le projet. Pour plus d’informations sur les programmes d’installation, consultez [déploiement d’Applications, Services et composants](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Vous pouvez également ajouter le code à votre projet pour vérifier si le schéma dans la bibliothèque et inscrit. Si elle n’est pas le cas, vous pouvez avertir l’utilisateur.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : mapper des schémas à des Documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Guide pratique pour mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  