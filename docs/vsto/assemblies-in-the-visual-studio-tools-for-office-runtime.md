---
title: Assemblys dans Visual Studio Tools pour Office Runtime | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- office-development
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 22750553e714c0aa02577ee95753e7d5b2bf13f4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys dans Visual Studio Tools pour Office Runtime
  Lorsque vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilisés pour le type de projet et la version .NET Framework cible du projet. Il existe différents assemblys dans les extensions Office pour .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour plus d’informations sur les extensions Office, consultez [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assemblys des extensions Office pour .NET Framework 4 et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour plus d’informations sur les espaces de noms et les types dans ces assemblys, consultez [référence managée & #40 ; développement Office dans Visual Studio & #41 ;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nom de l'assembly|Description|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fournit les types suivants :<br /><br /> -Les types pour la création de personnalisations de ruban et des balises actives. **Remarque :** balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Les types pour la création de volets actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les Compléments VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Excel, ainsi que des types de prise en charge. Pour plus d'informations, consultez [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fournit des types que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Word, ainsi que des types de prise en charge. Pour plus d'informations, consultez [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fournit les types suivants :<br /><br /> -Les exceptions pouvant être levées par Visual Studio Tools pour Office runtime.<br />-Zones de formulaire attributs, que vous pouvez utiliser lors de la création d’Outlook.|  
|Microsoft.Office.Tools.dll|Fournit des types faisant partie de l'infrastructure d'exécution Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fournit les types suivants :<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut et <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, vous pouvez utiliser pour le cache des objets de données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).<br />-La <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface que vous pouvez implémenter pour exécuter des étapes d’installation supplémentaires comme dernière étape du programme d’installation ClickOnce pour une solution Office. Pour plus d’informations, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Les exceptions pouvant être levées par Visual Studio Tools pour Office runtime.<br />-Les autres types faisant partie de Visual Studio Tools pour l’infrastructure du runtime Office et ne sont pas destinés à être utilisée directement depuis votre code.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fournit les types suivants :<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), que vous pouvez utiliser pour joindre des assemblys de personnalisation aux documents et accéder aux données mises en cache dans les documents. Pour plus d'informations, consultez [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie de mise en cache des données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] font également référence aux assemblys suivants. Ces assemblys ne font pas partie du package redistribuable [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ils dépendent d'assemblys qui doivent être déployés avec votre solution. Par défaut, ils sont copiés dans le dossier de sortie de génération de votre projet (la propriété **Copie locale** de ces assemblys a la valeur **True**). Si vous déployez votre projet à l'aide de ClickOnce, ces assembly sont inclus dans le package généré.  
  
|Nom de l'assembly|Description|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fournit les classes de base pour la classe `ThisAddIn` générée dans les projets de complément VSTO et la classe Ribbon générée dans tous les projets.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour le texte généré `ThisWorkbook` et `Sheet` dans les classes au niveau du document projets pour Excel.<br />-Contrôles Windows Forms que vous pouvez utiliser des feuilles de calcul dans les projets Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fournit des classes de base pour les classes `ThisAddIn` et de zone de formulaire générées dans les projets Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour le texte généré `ThisDocument` classe dans les projets au niveau du document pour Word.<br />-Contrôles Windows Forms que vous pouvez utiliser sur des documents dans les projets Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys des extensions Office pour .NET Framework 3.5  
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour .NET Framework 3.5. Pour obtenir de la documentation sur les espaces de noms et les classes de ces assemblys, consultez la section de référence suivante dans la documentation de Visual Studio 2008 : [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nom de l'assembly|Description|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fournit les types suivants :<br /><br /> -Microsoft.Office.Tools.AddIn classe de base pour les Compléments VSTO.<br />-Classes permettant de créer des personnalisations de ruban et des balises actives. **Remarque :** balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Classes pour la création de volets actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les Compléments VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Excel. Pour plus d'informations, consultez [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fournit des classes que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Word. Pour plus d'informations, consultez [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fournit les types suivants :<br /><br /> -La classe Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent, qui fournit les fonctions de liaison de données pour les contrôles hôtes dans les personnalisations au niveau du document.<br />-Les autres types faisant partie de Visual Studio Tools pour l’infrastructure du runtime Office et ne sont pas destinés à être utilisée directement depuis votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fournit les types suivants :<br /><br /> -Le Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute attribut et l’interface Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType, que vous pouvez utiliser pour le cache des objets de données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).<br />-Les exceptions pouvant être levées par Visual Studio Tools pour Office runtime.<br />-Les autres types faisant partie de Visual Studio Tools pour l’infrastructure du runtime Office et ne sont pas destinés à être utilisée directement depuis votre code.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fournit l’interface Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction, que vous pouvez implémenter pour exécuter des étapes d’installation supplémentaires comme dernière étape du programme d’installation ClickOnce pour une solution Office. Pour plus d'informations, consultez [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fournit les types suivants :<br /><br /> -La classe Microsoft.VisualStudio.Tools.Applications.ServerDocument, que vous pouvez utiliser pour joindre par programmation des assemblys de personnalisation aux documents et accéder aux données mises en cache dans les documents. Pour plus d'informations, consultez [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie de mise en cache des données dans une personnalisation au niveau du document. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fournit les types suivants :<br /><br /> -Les classes Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList et Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, vous pouvez utiliser pour créer des entrées de liste pour accorder une confiance à Office inclusion de l’utilisateur solutions qui ciblent le .NET Framework 3.5.<br />-Les autres types faisant partie de Visual Studio Tools pour l’infrastructure du runtime Office et ne sont pas destinés à être utilisée directement depuis votre code.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Scénarios d’installation de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  