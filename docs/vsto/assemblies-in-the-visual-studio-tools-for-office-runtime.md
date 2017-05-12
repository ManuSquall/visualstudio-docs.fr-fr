---
title: "Assemblys dans Visual Studio Tools pour Office Runtime"
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
  - "Visual Studio Tools pour Office Runtime, assemblys"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Assemblys dans Visual Studio Tools pour Office Runtime
  Lorsque vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilisés pour le type de projet et la version .NET Framework cible du projet. Il existe différents assemblys dans les extensions Office pour .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour plus d’informations sur les extensions Office, consultez [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Assemblys des extensions Office pour .NET Framework 4 et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour obtenir une documentation sur les espaces de noms et les types dans ces assemblys, consultez [Référence managée &#40;développement Office dans Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nom de l'assembly|Description|  
|-----------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fournit les types suivants :<br /><br /> -   Types pour la création de personnalisations du ruban et de balises actives. **Note:**      Les balises actives ne sont plus utilisées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Types pour la création de volets Actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les compléments VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Excel, ainsi que des types de prise en charge. Pour plus d'informations, consultez [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fournit des types que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Word, ainsi que des types de prise en charge. Pour plus d'informations, consultez [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fournit les types suivants :<br /><br /> -   Exceptions pouvant être levées par le runtime Visual Studio Tools pour Office.<br />-   Attributs que vous pouvez utiliser lors de la création de zones de formulaire Outlook.|  
|Microsoft.Office.Tools.dll|Fournit des types faisant partie de l'infrastructure d'exécution Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fournit les types suivants :<br /><br /> -   Attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> et interface <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, que vous pouvez utiliser pour mettre en cache des objets de données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Mise en cache des données](../vsto/caching-data.md).<br />-   Interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, que vous pouvez implémenter pour exécuter des étapes d'installation supplémentaires comme dernière étape du programme d'installation ClickOnce pour une solution Office. Pour plus d'informations, consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-   Exceptions pouvant être levées par le runtime Visual Studio Tools pour Office.<br />-   Autres types faisant partie de l'infrastructure du runtime Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fournit les types suivants :<br /><br /> -   Classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, que vous pouvez utiliser pour joindre des assemblys de personnalisation aux documents et accéder aux données mise en cache dans les documents. Pour plus d'informations, consultez [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Plusieurs classes qui représentent la hiérarchie de données mises en cache dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] font également référence aux assemblys suivants. Ces assemblys ne font pas partie du package redistribuable [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ils dépendent d'assemblys qui doivent être déployés avec votre solution. Par défaut, ils sont copiés dans le dossier de sortie de génération de votre projet \(la propriété **Copie locale** de ces assemblys a la valeur **True**\). Si vous déployez votre projet à l'aide de ClickOnce, ces assembly sont inclus dans le package généré.  
  
|Nom de l'assembly|Description|  
|-----------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fournit les classes de base pour la classe `ThisAddIn` générée dans les projets de complément VSTO et la classe Ribbon générée dans tous les projets.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -   Classes de base pour les classes `ThisWorkbook` et `Sheet` générées dans les projets de niveau document pour Excel.<br />-   Contrôles Windows Forms que vous pouvez utiliser sur les feuilles de calcul dans les projets Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fournit des classes de base pour les classes `ThisAddIn` et de zone de formulaire générées dans les projets Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -   Classes de base pour la classe `ThisDocument` générée dans les projets de niveau document pour Word.<br />-   Contrôles Windows Forms que vous pouvez utiliser sur les documents dans les projets Word.|  
  
## Assemblys des extensions Office pour .NET Framework 3.5  
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour .NET Framework 3.5. Pour obtenir de la documentation sur les espaces de noms et les classes de ces assemblys, consultez la section de référence suivante dans la documentation de Visual Studio 2008 : [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nom de l'assembly|Description|  
|-----------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fournit les types suivants :<br /><br /> -   Classe de base Microsoft.Office.Tools.AddIn pour les compléments VSTO.<br />-   Classes pour la création de personnalisations du ruban et de balises actives. **Note:**      Les balises actives ne sont plus utilisées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Classes pour la création de volets Actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les compléments VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Excel. Pour plus d'informations, consultez [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fournit des classes que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Word. Pour plus d'informations, consultez [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fournit les types suivants :<br /><br /> -   Classe Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent qui fournit les fonctions de liaison de données pour les contrôles hôtes dans les personnalisations au niveau du document.<br />-   Autres types faisant partie de l'infrastructure du runtime Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fournit les types suivants :<br /><br /> -   Attribut Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute et interface Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType, que vous pouvez utiliser pour mettre en cache des objets de données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Mise en cache des données](../vsto/caching-data.md).<br />-   Exceptions pouvant être levées par le runtime Visual Studio Tools pour Office.<br />-   Autres types faisant partie de l'infrastructure du runtime Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fournit l'interface Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction que vous pouvez implémenter pour exécuter des étapes d'installation supplémentaires comme dernière étape du programme d'installation ClickOnce pour une solution Office. Pour plus d'informations, consultez [Déploiement avancé de solutions Office](http://msdn.microsoft.com/fr-fr/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fournit les types suivants :<br /><br /> -   Classe Microsoft.VisualStudio.Tools.Applications.ServerDocument, que vous pouvez utiliser pour joindre par programmation des assemblys de personnalisation aux documents et accéder aux données mise en cache dans les documents. Pour plus d'informations, consultez [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Plusieurs classes qui représentent la hiérarchie de données mises en cache dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fournit les types suivants :<br /><br /> -   Classes Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry et Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, que vous pouvez utiliser pour créer des entrées de liste d'inclusion de l'utilisateur pour accorder un niveau de confiance à des solutions Office qui ciblent .NET Framework 3.5.<br />-   Autres types faisant partie de l'infrastructure du runtime Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
  
## Voir aussi  
 [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Scénarios d'installation de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  