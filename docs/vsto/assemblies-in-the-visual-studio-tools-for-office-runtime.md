---
title: Assemblys dans Visual Studio Tools pour Office runtime
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
ms.openlocfilehash: 1e4d9932e64cbbd862c5784073ed4dbe7cb85709
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628284"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys dans Visual Studio Tools pour Office runtime
  Lorsque vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilisés pour le type de projet et la version .NET Framework cible du projet. Il existe différents assemblys dans les extensions Office pour .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour plus d’informations sur les extensions Office, consultez [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assemblys dans les extensions Office pour .NET Framework 4 et le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Pour obtenir une documentation sur les espaces de noms et les types dans ces assemblys, consultez [référence managée &#40;développement Office dans Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Fournit les types suivants :<br /><br /> -Types pour la création de personnalisations du ruban et des balises actives. **Remarque :**      Les balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Types pour la création de volets actions dans les personnalisations au niveau du document et les volets de tâches personnalisés dans les Compléments VSTO.|
|Microsoft.Office.Tools.Excel.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Excel, ainsi que des types de prise en charge. Pour plus d’informations, consultez [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Fournit des types que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|
|Microsoft.Office.Tools.Word.dll|Fournit des interfaces qui représentent des éléments hôtes et des contrôles hôtes pour les projets Word, ainsi que des types de prise en charge. Pour plus d’informations, consultez [automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Fournit les types suivants :<br /><br /> -Les exceptions qui peuvent être levées par Visual Studio Tools pour Office runtime.<br />-Vous pouvez utiliser lors de la création d’Outlook des attributs des zones de formulaire.|
|Microsoft.Office.Tools.dll|Fournit des types faisant partie de l'infrastructure d'exécution Visual Studio Tools pour Office et qui ne sont pas conçus pour être utilisés directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fournit les types suivants :<br /><br /> -Le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut et <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, vous pouvez utiliser pour le cache des objets de données dans une personnalisation au niveau du document. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).<br />-Le <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface, que vous pouvez implémenter pour exécuter des étapes d’installation supplémentaires comme l’étape finale du programme d’installation ClickOnce pour une solution Office. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Les exceptions qui peuvent être levées par Visual Studio Tools pour Office runtime.<br />-Autres types qui font partie de Visual Studio Tools pour l’infrastructure de runtime d’Office et ne sont pas destinées à être utilisées directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fournit les types suivants :<br /><br /> -Le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), que vous pouvez utiliser pour joindre des assemblys de personnalisation aux documents et accéder aux données mises en cache dans les documents. Pour plus d’informations, consultez [gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie de mise en cache des données dans une personnalisation au niveau du document. Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|

 Les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] font également référence aux assemblys suivants. Ces assemblys ne font pas partie du package redistribuable [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Ils dépendent d'assemblys qui doivent être déployés avec votre solution. Par défaut, ils sont copiés dans le dossier de sortie de génération de votre projet (la propriété **Copie locale** de ces assemblys a la valeur **True**). Si vous déployez votre projet à l'aide de ClickOnce, ces assembly sont inclus dans le package généré.

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fournit les classes de base pour la classe `ThisAddIn` générée dans les projets de complément VSTO et la classe Ribbon générée dans tous les projets.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour le texte généré `ThisWorkbook` et `Sheet` dans les classes au niveau du document projets pour Excel.<br />-Contrôles Windows Forms que vous pouvez utiliser sur des feuilles de calcul dans les projets Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fournit des classes de base pour les classes `ThisAddIn` et de zone de formulaire générées dans les projets Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fournit les types suivants :<br /><br /> -Classes de base pour le texte généré `ThisDocument` classe dans les projets au niveau du document pour Word.<br />-Contrôles Windows Forms que vous pouvez utiliser sur des documents dans les projets Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys dans les extensions Office pour .NET Framework 3.5
 Le tableau suivant répertorie les assemblys inclus dans les extensions Office pour .NET Framework 3.5. Pour obtenir une documentation sur les espaces de noms et les classes dans ces assemblys, consultez la section de référence suivante dans la documentation de Visual Studio 2008 : [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).

|Nom de l'assembly|Description|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Fournit les types suivants :<br /><br /> -Microsoft.Office.Tools.AddIn classe de base pour les Compléments VSTO.<br />-Classes pour la création de personnalisations du ruban et des balises actives. **Remarque :**      Les balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Classes pour la création de volets actions dans les personnalisations au niveau du document et les volets Office personnalisés dans des Compléments VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Excel. Pour plus d’informations, consultez [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fournit des classes que vous pouvez utiliser pour créer des zones de formulaire personnalisées dans les compléments VSTO Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Fournit des éléments hôtes et des contrôles hôtes pour les solutions Word. Pour plus d’informations, consultez [automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Fournit les types suivants :<br /><br /> -Le [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) (classe), qui fournit les fonctionnalités de liaison de données pour les personnalisations de niveau document de contrôles hôtes dans.<br />-Autres types qui font partie de Visual Studio Tools pour l’infrastructure de runtime d’Office et ne sont pas destinées à être utilisées directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fournit les types suivants :<br /><br /> -Le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut et <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, vous pouvez utiliser pour le cache des objets de données dans une personnalisation au niveau du document. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).<br />-Les exceptions qui peuvent être levées par Visual Studio Tools pour Office runtime.<br />-Autres types qui font partie de Visual Studio Tools pour l’infrastructure de runtime d’Office et ne sont pas destinées à être utilisées directement à partir de votre code.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fournit l'interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> que vous pouvez implémenter pour exécuter des étapes d'installation supplémentaires comme dernière étape du programme d'installation ClickOnce pour une solution Office. Pour plus d’informations, consultez [déploiement d’une solution Office Advanced](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fournit les types suivants :<br /><br /> -Le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), que vous pouvez utiliser pour joindre par programmation des assemblys de personnalisation aux documents et accéder aux données mises en cache dans les documents. Pour plus d’informations, consultez [gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Plusieurs classes qui représentent la hiérarchie de mise en cache des données dans une personnalisation au niveau du document. Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fournit les types suivants :<br /><br /> -Les classes Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList et Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, que vous pouvez utiliser pour créer des entrées de liste pour accorder une confiance à Office d’inclusion de l’utilisateur solutions qui ciblent le .NET Framework 3.5.<br />-Autres types qui font partie de Visual Studio Tools pour l’infrastructure de runtime d’Office et ne sont pas destinées à être utilisées directement à partir de votre code.|

## <a name="see-also"></a>Voir aussi
- [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools pour les scénarios d’installation Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
