---
title: Automatisation d’Excel à l’aide d’objets étendus | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7c1111a9fdd66d99f1dda40d3045ad337d499a6a
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="automating-excel-by-using-extended-objects"></a>Automatisation d'Excel à l'aide d'objets étendus
  Quand vous développez des solutions Excel dans Visual Studio, vous pouvez également utiliser les *éléments hôtes* et les *contrôles hôtes*dans vos solutions. Il s'agit d'objets qui étendent certains objets couramment utilisés dans le modèle objet Excel (autrement dit, le modèle objet exposé par l'assembly PIA (Primary Interop Assembly) pour Excel), par exemple les objets <xref:Microsoft.Office.Interop.Excel.Worksheet> et <xref:Microsoft.Office.Interop.Excel.Range> . Les objets étendus se comportent comme les objets Excel dont ils dépendent. Toutefois, ils ajoutent des fonctionnalités supplémentaires telles que de nouveaux événements et la liaison de données aux objets.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Les éléments hôtes et les contrôles hôtes sont disponibles dans les compléments VSTO et les personnalisations au niveau du document. Toutefois, le contexte dans lequel ils peuvent être utilisés est différent pour chaque type de solution. Pour plus d'informations, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="excel-host-items"></a>Éléments hôtes Excel  
 Les projets Excel vous permettent d'accéder à plusieurs éléments hôtes :  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Cet élément hôte contient une feuille de calcul dans votre projet. Il sert également de conteneur pour les contrôles managés, notamment les contrôles hôtes et les contrôles Windows Forms. En outre, il gère les informations relatives aux contrôles sur sa surface. Pour plus d'informations, consultez [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Cet élément hôte représente le classeur de votre projet. Il sert de conteneur pour les composants partagés par toutes les feuilles de calcul du classeur. Pour plus d'informations, consultez [Workbook Host Item](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Cet élément hôte est une feuille de calcul Excel qui contient uniquement un graphique et expose des événements.  
  
     Quand vous ajoutez une feuille de graphique au moment du design en tant que nouvelle feuille dans votre projet de personnalisation au niveau du document Microsoft Office Excel, Visual Studio crée automatiquement un élément hôte <xref:Microsoft.Office.Tools.Excel.ChartSheet> .  
  
     Bien qu'un élément hôte <xref:Microsoft.Office.Tools.Excel.ChartSheet> soit une feuille de calcul Excel, vous ne pouvez pas ajouter de contrôles à la feuille de graphique. Si vous souhaitez disposer d'autres contrôles sur une feuille de calcul avec un graphique, n'utilisez pas une feuille de graphique. Placez plutôt un graphique en tant qu'objet incorporé dans une feuille de calcul à l'aide du contrôle hôte <xref:Microsoft.Office.Tools.Excel.Chart> . Pour plus d'informations, consultez [Chart Control](../vsto/chart-control.md).  
  
## <a name="excel-host-controls"></a>Contrôles hôtes Excel  
 Il existe plusieurs contrôles hôtes pour Excel qui vous aident à créer, organiser et automatiser des classeurs et des feuilles de calcul. Ces contrôles hôtes fournissent des événements et des fonctionnalités de liaison de données dont ne disposent pas leurs équivalents dans le modèle objet Excel natif.  
  
 Pour plus d'informations sur les contrôles hôtes que vous pouvez utiliser dans les projets Excel, consultez les rubriques suivantes :  
  
-   [Chart Control](../vsto/chart-control.md)  
  
-   [ListObject, contrôle](../vsto/listobject-control.md)  
  
-   [NamedRange, contrôle](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange, contrôle](../vsto/xmlmappedrange-control.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : remplir de données des contrôles ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Comment : ajouter des contrôles Chart aux feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Comment : mapper des colonnes ListObject aux données](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Procédure pas à pas : Programmation d’événements d’un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  