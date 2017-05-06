---
title: "Sch&#233;mas et donn&#233;es XML dans les personnalisations au niveau du document"
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
  - "développement Office dans Visual Studio, XML"
  - "schémas (développement Office dans Visual Studio)"
  - "XML (développement Office dans Visual Studio), schémas XML"
  - "schémas XML (développement Office dans Visual Studio)"
  - "schémas XML (développement Office dans Visual Studio), à propos des données et des schémas XML"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Sch&#233;mas et donn&#233;es XML dans les personnalisations au niveau du document
  **important** les informations présentées dans cette rubrique concernant Microsoft Word est présenté exclusivement pour l'avantage et l'utilisation des personnes et organisations qui se trouvent en dehors de les états\-unis et de ses territoires ou qui utilisent, ou de développer des programmes qui s'exécutent sur, les produits Microsoft Word qui ont été autorisés par Microsoft avant janvier 2010, lorsque Microsoft a supprimé une implémentation de fonctionnalités spécifique liée à une personnalisée XML Microsoft Word.  Ces informations liées à Microsoft Word ne peuvent pas être lues ou utilisées par des individus ou des organisations se trouvant aux États\-Unis ou dans ses territoires qui utilisent, ou développent des programmes exécutés avec, des produits Microsoft Word dont la licence Microsoft est postérieure à janvier 2010 ; ces produits n'auront pas le même comportement que ceux dont la licence est antérieure à cette date ou ceux qui ont été achetés ou ont bénéficié d'une licence d'utilisation en dehors des États\-Unis.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel et Microsoft Office Word proposent une fonctionnalité qui permet de mapper des schémas à vos documents.  Cette fonctionnalité peut simplifier l'importation et l'exportation de données XML vers et depuis les documents en question.  
  
 Visual Studio expose des éléments de schéma mappés dans des personnalisations au niveau du document sous forme de contrôles dans le modèle de programmation.  Dans Excel, Visual Studio prend en charge la liaison des contrôles aux données dans les bases de données, les services Web et les objets.  Dans Word et Excel, Visual Studio prend en charge des volets Actions, qui peuvent être utilisés avec un document mappé par schéma afin d'améliorer l'expérience de l'utilisateur final qui utilise vos solutions.  Pour plus d’informations, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser des schémas XML multipart dans les solutions Excel.  
  
## Objets créés lorsque les schémas sont joints aux classeurs Excel  
 Lorsque vous joignez un schéma à un classeur, Visual Studio crée automatiquement plusieurs objets et les ajoute à votre projet.  Ces objets ne doivent pas être supprimés à l'aide d'outils Visual Studio car ils sont gérés par Excel.  Pour les supprimer, retirez les éléments mappés de la feuille de calcul ou détachez le schéma à l'aide des outils Excel.  
  
 Il existe deux objets principaux :  
  
-   Schéma XML \(fichier XSD\).  Pour chaque schéma du classeur, Visual Studio ajoute un schéma au projet.  Celui\-ci apparaît comme un élément de projet avec une extension XSD dans l'**Explorateur de solutions**.  
  
-   Classe <xref:System.Data.DataSet> typée.  Cette classe est créée en fonction du schéma.  Cette classe DataSet est visible dans **Affichage de classes**.  
  
## Objets créés lorsque les éléments de schéma sont mappés aux feuilles de calcul Excel  
 Lorsque vous mappez un élément de schéma du volet de tâches **Source XML** à une feuille de calcul, Visual Studio crée automatiquement plusieurs objets et les ajoute à votre projet :  
  
-   Contrôles.  Pour chaque objet mappé dans le classeur, un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> \(pour les éléments de schéma non répétitifs\) ou un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> \(pour les éléments de schéma répétitifs\) est créé dans le modèle de programmation.  Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut être supprimé uniquement en supprimant les mappages et les objets mappés du classeur.  Pour plus d'informations sur les contrôles, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource.  Lorsque vous créez un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> en mappant un élément de schéma non récurrent à la feuille de calcul, un <xref:System.Windows.Forms.BindingSource> est créé et le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est lié au <xref:System.Windows.Forms.BindingSource>.  Vous devez lier le <xref:System.Windows.Forms.BindingSource> à une instance de la source de données qui correspond au schéma mappé au document, comme une instance de la classe <xref:System.Data.DataSet> typée qui a été créée.  Créez la liaison en définissant les propriétés <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> qui sont exposées dans la fenêtre **Propriétés**.  
  
    > [!NOTE]  
    >  Le <xref:System.Windows.Forms.BindingSource> n'est pas créé pour les objets <xref:Microsoft.Office.Tools.Excel.ListObject>.  Vous devez lier manuellement le <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données à l'aide des propriétés <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> de la fenêtre **Propriétés**.  
  
### Schémas mappés Office et fenêtre Sources de données Visual Studio  
 Les fonctionnalités de schéma mappé d'Office et la fenêtre **Sources de données** de Visual Studio peuvent vous aider à présenter des données sur une feuille de calcul Excel pour la modification ou la création de rapports.  Dans les deux cas, vous pouvez faire glisser des éléments de données sur la feuille de calcul Excel.  Les deux méthodes créent des contrôles qui sont liés aux données via un <xref:System.Windows.Forms.BindingSource> dans une source de données telle qu'un <xref:System.Data.DataSet> ou un service Web.  
  
> [!NOTE]  
>  Lorsque vous mappez un élément de schéma répétitif à une feuille de calcul, Visual Studio crée un <xref:Microsoft.Office.Tools.Excel.ListObject>.  Le <xref:Microsoft.Office.Tools.Excel.ListObject> n'est pas lié automatiquement aux données via le <xref:System.Windows.Forms.BindingSource>.  Vous devez lier manuellement le <xref:Microsoft.Office.Tools.Excel.ListObject> à la source de données à l'aide des propriétés <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> de la fenêtre **Propriétés**.  
  
 Le tableau suivant présente une série de différences entre les deux méthodes.  
  
|Schéma XML|Fenêtre Sources de données|  
|----------------|--------------------------------|  
|Utilise l'interface Office.|Utilise la fenêtre **Sources de données** dans Visual Studio.|  
|Active les fonctionnalités Office intégrées pour importer et exporter des données de fichiers XML.|Vous devez fournir par programme des fonctionnalités d'importation et d'exportation.|  
|Vous devez écrire du code pour remplir les contrôles générés avec des données.|Le code des contrôles ajoutés à partir de la fenêtre **Sources de données** est généré automatiquement pour les remplir, ainsi que les chaînes de connexion nécessaires lorsque vous utilisez des serveurs de base de données.|  
  
## Comportement lorsque les schémas sont joints aux documents Word  
 Aucun objet de données n'est créé lorsque vous attachez un schéma à un document Word utilisé dans un projet Office au niveau du document.  Toutefois, lorsque vous mappez un élément de schéma à votre document, des contrôles sont créés.  Le type de contrôle dépend du type d'élément que vous mappez ; les éléments répétitifs génèrent des contrôles <xref:Microsoft.Office.Tools.Word.XMLNodes>, et les éléments non répétitifs génèrent des contrôles <xref:Microsoft.Office.Tools.Word.XMLNode>.  Pour plus d'informations, consultez [XMLNodes, contrôle](../vsto/xmlnodes-control.md) et [XMLNode, contrôle](../vsto/xmlnode-control.md).  
  
## Déploiement de solutions qui incluent des schémas XML  
 Vous devez créer un programme d'installation pour déployer une solution qui utilise un schéma XML mappé à un document.  Le programme d'installation doit enregistrer le schéma dans la bibliothèque de schémas sur l'ordinateur de l'utilisateur.  Si vous n'enregistrez pas le schéma, la solution fonctionne encore car Word génère un schéma temporaire basé sur les éléments qui sont dans le document lorsque l'utilisateur l'ouvre.  Toutefois, l'utilisateur ne peut pas effectuer une validation ou enregistrer le schéma utilisé pour créer le projet.  Pour plus d'informations sur les programmes d'installation, consultez [Déploiement d'applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).  
  
 Vous pouvez également ajouter du code à votre projet pour vérifier si le schéma est dans la bibliothèque et s'il est enregistré.  Si ce n'est pas le cas, vous pouvez avertir l'utilisateur.  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## Voir aussi  
 [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  