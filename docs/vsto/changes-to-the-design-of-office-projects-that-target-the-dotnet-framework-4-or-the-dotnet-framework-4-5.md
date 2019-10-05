---
title: Conception des modifications apportées aux projets Office ciblant .NET Framework
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74cb79a68298bb1c544b0f0646787e82e04cb810
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255173"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Modifications apportées à la conception des projets Office qui ciblent le .NET Framework 4 ou le .NET Framework 4,5
  Depuis [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio a introduit des modifications à la conception des projets Office ciblant le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Si vous avez déjà travaillé avec des projets Office dans les versions antérieures de Visual Studio, vous devez tenir compte de ces modifications avant de développer des projets Office ciblant ces versions du .NET Framework 4.0 ou version ultérieure. Par défaut, tous les projets que vous créez à l'aide de Visual Studio 2013 ou version ultérieure ciblent le .NET Framework 4.0 ou version ultérieure.

 Les sections suivantes décrivent les modifications apportées à la conception des projets Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Comprendre la conception basée sur l’interface de Visual Studio 2010 Tools pour Office Runtime
 Lorsque vous développez un projet Office qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] le ou version ultérieure, la plupart des types que vous utilisez dans Visual Studio 2010 Tools pour Office Runtime sont des interfaces. Ceci constitue un changement majeur par rapport aux versions antérieures de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], dans lesquelles ces types étaient des classes. Par exemple, quand vous ciblez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, les types <xref:Microsoft.Office.Tools.Excel.Worksheet> et <xref:Microsoft.Office.Tools.Word.Document> sont des interfaces, et non des classes. Pour plus d’informations, consultez [vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Pour tous les types que vous pouviez instancier directement dans les versions antérieures de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], vous devez maintenant utiliser des méthodes de l'objet `Globals.Factory` pour obtenir des instances de ces types. Par exemple, pour obtenir un objet qui implémente l'interface <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilisez la méthode `Globals.Factory.CreateSmartTag`. Pour plus d’informations, consultez les rubriques suivantes :

- [Mettez à jour les projets Excel et Word que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Mettre à jour les personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Mettez à jour les zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nouvelles classes de base dans les projets Office
 La nouvelle conception basée sur l’interface de Visual Studio 2010 Tools pour Office Runtime affecte les classes générées dans les projets Office, `ThisDocument`tels `ThisWorkbook`que, `ThisAddIn`et. Dans les projets Office qui ciblent le .NET Framework 3.5 et versions antérieures, ces classes générées dérivent de classes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] telles que `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet` et `Microsoft.Office.Tools.AddIn`. Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces classes [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sont désormais des interfaces. Par conséquent, les classes générées dans les projets Office ne peuvent plus en dériver leur implémentation. Au lieu de cela, les classes générées dérivent de nouvelles classes de base telles que <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>et <xref:Microsoft.Office.Tools.AddInBase>. Pour plus d’informations, consultez [programmer des compléments VSTO](../vsto/programming-vsto-add-ins.md) et [programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

 Les classes de base ne font pas partie du composant redistribuable [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Au lieu de cela, elles sont définies dans les assemblys d'utilitaires inclus dans Visual Studio. Ces assemblys, qui sont copiés dans le dossier de sortie quand vous générez des projets Office, doivent être déployés avec votre solution. Pour plus d’informations sur les assemblys d’utilitaires, consultez [assemblys dans le Visual Studio Tools pour Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Modifications avec rupture dans les projets Office reciblés sur le .NET Framework 4
 Le tableau suivant répertorie les principales modifications avec rupture que vous pouvez rencontrer dans les projets Office reciblés vers le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Pour plus d’informations, consultez [migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Modification avec rupture|Conséquence|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> n'est plus utilisé ni pris en charge dans les projets Office.|Vous devez supprimer cet attribut du fichier de code AssemblyInfo dans les projets Office que vous mettez à niveau depuis Visual Studio 2008. Pour plus d’informations, consultez [modifications requises pour exécuter des projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Le **attribut excellocale1033** n’est plus utilisé ni pris en charge dans les projets Excel.|Vous devez supprimer cet attribut du fichier de code *AssemblyInfo* dans les projets Excel. Pour plus d’informations, consultez [mettre à jour les projets Excel et Word à migrer vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Le modèle de programmation des éléments de projet **Ruban (Concepteur visuel)** a changé.|Vous devez modifier le fichier code-behind pour tous les éléments du ruban dans votre projet. Vous devez également modifier tout code qui instancie des contrôles de ruban au moment de l’exécution, qui gère les événements de ruban ou qui définit la position d’un composant de ruban par programmation. Pour plus d’informations, consultez [mettre à jour les personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5).|
|Le modèle de programmation des zones de formulaire Outlook a changé.|Vous devez modifier le fichier code-behind pour toutes les zones de formulaire de votre projet et tout code qui instancie certaines classes de zone de formulaire au moment de l'exécution. Pour plus d’informations, consultez [mettre à jour les zones de formulaire dans les projets Outlook que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Le modèle de programmation des balises actives dans les projets Excel et Word a changé. Les balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Si votre solution utilise des balises actives, des erreurs se produisent quand vous générez le projet. Étant donné que les balises actives sont déconseillées dans [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] et [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], vous devez supprimer les balises avant de pouvoir tester et déboguer la solution dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ou version ultérieure.|
|La syntaxe des méthodes `GetVstoObject` et `HasVstoObject` a changé.|Vous devez passer l'objet `Globals.Factory` à ces méthodes quand vous y accéder sur les objets natifs depuis les assemblys PIA (Primary Interop Assemblies). Vous pouvez également accéder à ces méthodes sur l'objet retourné par la propriété `Globals.Factory` dans votre projet. Pour plus d’informations, consultez [mettre à jour les projets Excel et Word à migrer vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Les événements de contrôles de contenu Word sont associés à de nouveaux délégués.|Vous devez modifier tout code qui gère les événements de contrôles de contenu Word pour spécifier les nouveaux délégués. Pour plus d’informations, consultez [mettre à jour les projets Excel et Word à migrer vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Les classes `OLEObject` et `OLEControl` ont été renommées.|Vous devez modifier tout code qui utilise des instances de ces classes et utiliser à la place des objets <xref:Microsoft.Office.Tools.Excel.ControlSite> ou <xref:Microsoft.Office.Tools.Word.ControlSite> . Pour plus d’informations, consultez [mettre à jour les projets Excel et Word à migrer vers le .NET Framework 4 ou le .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Les classes d’élément hôte, `ThisWorkbook`telles `Sheet`que, `ThisDocument` *n*, `ThisAddIn`et, ne fournissent plus `Dispose` de méthode que vous pouvez substituer.|Vous devez déplacer tout code dans la substitution de méthode `Dispose` vers le gestionnaire d'événements `Shutdown` dans la classe d'élément hôte, par exemple, `ThisAddIn_Shutdown`, et supprimer la substitution de méthode `Dispose` de votre classe d'élément hôte.|

## <a name="see-also"></a>Voir aussi
- [Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Nouveautés du développement Office](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)
- [Vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
