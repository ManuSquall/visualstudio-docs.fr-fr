---
title: Assemblys dans le Visual Studio Tools pour Office Runtime
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b2fc47aa917fa9c9d5351fd313ec46ae4aaa0664
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918781"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys dans le Visual Studio Tools pour Office Runtime
  Lorsque vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] utilisés pour le type de projet et la version .NET Framework cible du projet. Il existe différents assemblys dans les extensions Office pour .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]et [!INCLUDE[net_v45](includes/net-v45-md.md)]. Pour plus d’informations sur les extensions Office, consultez [vue d’ensemble de Visual Studio Tools pour Office Runtime](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenet_v45includesnet-v45-mdmd"></a>Assemblys dans les extensions Office pour le .NET Framework 4 et le [!INCLUDE[net_v45](includes/net-v45-md.md)]
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et [!INCLUDE[net_v45](includes/net-v45-md.md)]. Pour obtenir de la documentation sur les espaces de noms et les types dans ces assemblys, consultez [ &#40;développement Office&#41;de référence managée dans Visual Studio](managed-reference-office-development-in-visual-studio.md).

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Fournit les types suivants :<br /><br /> -Types pour la création de personnalisations de ruban et de balises actives. **Remarque :**      Les balises actives sont dépréciées dans [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](includes/word-14-short-md.md)].<br />-Types pour la création de volets actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les compléments VSTO.|
|Microsoft.Office.Tools.Excel.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Excel, ainsi que des types de prise en charge. Pour plus d’informations, consultez [automatiser Excel à l’aide d’objets étendus](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Fournit des types que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|
|Microsoft.Office.Tools.Word.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Word, ainsi que des types de prise en charge. Pour plus d’informations, consultez [automatiser Word à l’aide d’objets étendus](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Fournit les types suivants :<br /><br /> -Exceptions qui peuvent être levées par le Visual Studio Tools pour Office Runtime.<br />-Attributs que vous pouvez utiliser lors de la création de zones de formulaire Outlook.|
|Microsoft.Office.Tools.dll|Fournit des types faisant partie de l'infrastructure d'exécution Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fournit les types suivants :<br /><br /> -L' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut et <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que vous pouvez utiliser pour mettre en cache des objets de données dans une personnalisation au niveau du document. Pour plus d’informations, consultez mettre [en cache les données](caching-data.md).<br />-L’interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, que vous pouvez implémenter pour exécuter des étapes d’installation supplémentaires comme dernière étape du programme d’installation ClickOnce pour une solution Office. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />-Exceptions qui peuvent être levées par le Visual Studio Tools pour Office Runtime.<br />-D’autres types qui font partie du Visual Studio Tools pour l’infrastructure d’exécution Office, et ne sont pas destinés à être utilisés directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fournit les types suivants :<br /><br /> -La classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, que vous pouvez utiliser pour attacher des assemblys de personnalisation aux documents et pour accéder aux données mises en cache dans les documents. Pour plus d’informations, consultez [gérer des documents sur un serveur à l’aide de la classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie des données mises en cache dans une personnalisation au niveau du document. Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](accessing-data-in-documents-on-the-server.md).|

 Les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](includes/net-v45-md.md)] font également référence aux assemblys suivants. Ces assemblys ne font pas partie du package redistribuable [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] . Ils dépendent d'assemblys qui doivent être déployés avec votre solution. Par défaut, ils sont copiés dans le dossier de sortie de génération de votre projet (la propriété **Copie locale** de ces assemblys a la valeur **True**). Si vous déployez votre projet à l'aide de ClickOnce, ces assembly sont inclus dans le package généré.

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fournit les classes de base pour la classe `ThisAddIn` générée dans les projets de complément VSTO et la classe Ribbon générée dans tous les projets.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour les classes `ThisWorkbook` et `Sheet` générées dans les projets au niveau du document pour Excel.<br />-Windows Forms les contrôles que vous pouvez utiliser dans les feuilles de calcul dans les projets Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fournit des classes de base pour les classes `ThisAddIn` et de zone de formulaire générées dans les projets Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour la classe de `ThisDocument` générée dans les projets au niveau du document pour Word.<br />-Windows Forms les contrôles que vous pouvez utiliser sur les documents dans les projets Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys dans les extensions Office pour le .NET Framework 3,5
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour .NET Framework 3.5. Pour obtenir de la documentation sur les espaces de noms et les classes de ces assemblys, consultez la section de référence suivante dans la documentation de Visual Studio 2008 : [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md).

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Fournit les types suivants :<br /><br /> -Classe de base Microsoft. Office. Tools. AddIn pour les compléments VSTO.<br />-Classes pour la création de personnalisations de ruban et de balises actives. **Remarque :**      Les balises actives sont dépréciées dans [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](includes/word-14-short-md.md)].<br />-Classes pour la création de volets actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les compléments VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Excel. Pour plus d’informations, consultez [automatiser Excel à l’aide d’objets étendus](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fournit des classes que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Word. Pour plus d’informations, consultez [automatiser Word à l’aide d’objets étendus](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Fournit les types suivants :<br /><br /> -La classe [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , qui fournit les fonctionnalités de liaison de données pour les contrôles hôtes dans les personnalisations au niveau du document.<br />-D’autres types qui font partie du Visual Studio Tools pour l’infrastructure d’exécution Office, et ne sont pas destinés à être utilisés directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fournit les types suivants :<br /><br /> -L' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut et <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que vous pouvez utiliser pour mettre en cache des objets de données dans une personnalisation au niveau du document. Pour plus d’informations, consultez mettre [en cache les données](caching-data.md).<br />-Exceptions qui peuvent être levées par le Visual Studio Tools pour Office Runtime.<br />-D’autres types qui font partie du Visual Studio Tools pour l’infrastructure d’exécution Office, et ne sont pas destinés à être utilisés directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fournit l'interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> que vous pouvez implémenter pour exécuter des étapes d'installation supplémentaires comme dernière étape du programme d'installation ClickOnce pour une solution Office. Pour plus d’informations, consultez [déploiement de solutions Office avancées](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fournit les types suivants :<br /><br /> -La classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, que vous pouvez utiliser pour attacher par programmation des assemblys de personnalisation aux documents et accéder aux données mises en cache dans les documents. Pour plus d’informations, consultez [gérer des documents sur un serveur à l’aide de la classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie des données mises en cache dans une personnalisation au niveau du document. Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fournit les types suivants :<br /><br /> -Les classes Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry et Microsoft. VisualStudio. Tools. Office. Runtime. Security. UserInclusionList, que vous pouvez utiliser pour créer des entrées de liste d’inclusion d’utilisateur pour accorder une confiance à Office les solutions qui ciblent le .NET Framework 3,5.<br />-D’autres types qui font partie du Visual Studio Tools pour l’infrastructure d’exécution Office, et ne sont pas destinés à être utilisés directement à partir de votre code.|

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble de Visual Studio Tools pour Office Runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools pour les scénarios d’installation d’Office Runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
