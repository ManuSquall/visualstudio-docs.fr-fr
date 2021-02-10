---
title: Propriétés dans les projets Office
description: En savoir plus sur les propriétés disponibles pour les projets Office dans Visual Studio à l’aide de l’Fenêtre Propriétés.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f7a2ab04e1926a53c3d3aa05023103206c6aa01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971763"
---
# <a name="properties-in-office-projects"></a>Propriétés dans les projets Office
  Plusieurs propriétés importantes peuvent être définies pour les projets Office dans Visual Studio. Ces propriétés sont disponibles dans la fenêtre **Propriétés** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Espace de noms pour l’élément hôte
 Utilisez la propriété **espace de noms de l’élément hôte** pour modifier l’espace de noms des classes d’élément hôte (par exemple, les `ThisAddIn` `ThisWorkbook` classes, ou `ThisDocument` ) dans les projets Visual C#. Cette propriété s’affiche dans la fenêtre **Propriétés** lorsque vous sélectionnez le nœud de document dans un projet au niveau du document (tel que *ExcelWorkbook1.xlsx* ou *WordDocument1.docx*) ou le nœud d’application dans un projet de complément VSTO (par exemple, Excel ou Word) dans **Explorateur de solutions**.

 Quand vous créez un projet Office Visual C#, un espace de noms basé sur le nom du projet est attribué aux éléments hôtes. Il est recommandé d'utiliser la propriété **Espace de noms de l'élément hôte** pour modifier l'espace de noms, plutôt que de modifier directement les fichiers de code. Quand vous utilisez cette propriété, l'espace de noms est modifié dans les fichiers de code générés (masqués), ainsi que dans les fichiers de code visibles.

## <a name="cacheindocument"></a>CacheInDocument
 La propriété **CacheInDocument** s'affiche dans la fenêtre **Propriétés** pour les projets de niveau document quand vous sélectionnez une instance de <xref:System.Data.DataSet> dans le concepteur Visual Studio. Seuls les membres publics peuvent être mis en cache. Vérifiez que la propriété **Modifiers** a la valeur **Public** si vous souhaitez mettre en cache <xref:System.Data.DataSet>.

 Cette propriété accepte une valeur booléenne :

- Choisissez **true** pour mettre le dataset en cache dans le document.

- Choisissez **false** si vous ne voulez pas que le dataset soit mis en cache dans le document.

  Pour plus d’informations sur la mise en cache des données, consultez [données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Value2
 La propriété **Value2** est uniquement disponible pour les projets de modèle ou de classeur Excel. Elle s'affiche sous le nœud de propriété **Databindings** dans la fenêtre **Propriétés** quand vous sélectionnez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans le concepteur de feuilles de calcul.

 Utilisez la propriété **Value2** dans la fenêtre **Propriétés** pour lier la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> de <xref:Microsoft.Office.Tools.Excel.NamedRange> à un champ dans la source de données.

## <a name="see-also"></a>Voir aussi
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)
- [Événements dans les projets Office](../vsto/events-in-office-projects.md)
