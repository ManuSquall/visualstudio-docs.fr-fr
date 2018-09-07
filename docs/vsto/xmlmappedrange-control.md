---
title: XmlMappedRange, contrôle
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9cf21ceda64fe79996e05426a3379972c3c4be33
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673052"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange, contrôle
  Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle est une plage qui est créée uniquement lorsqu’un élément de schéma non répétitif est mappé à une cellule dans Microsoft Office Excel. Par exemple, lorsque le `maxOccurs` attribut d’un élément de schéma est égal à 1. Une fois que Visual Studio crée la plage mappée XML, vous pouvez le programmer directement, sans devoir parcourir le modèle objet Excel. Vous ne pouvez supprimer un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle dans Excel lorsque le mappage d’élément est supprimé.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [comment effectuer un mappage de faire : utiliser le langage XML dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="bind-data-to-the-control"></a>Lier des données au contrôle  
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle prend en charge la liaison à un seul champ de données (liaison de données simple). Le <xref:Microsoft.Office.Tools.Excel.ListObject> peut de contrôle prend en charge la liaison de données complexe et est automatiquement créé lorsqu’un élément de schéma répétitif est mappé à une cellule. Pour plus d’informations, consultez [contrôle ListObject](../vsto/listobject-control.md).  
  
 Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle est lié à une source de données à l’aide de la <xref:System.Windows.Forms.Control.DataBindings%2A> propriété. Quand un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est ajouté à une cellule de feuille de calcul, Visual Studio génère automatiquement un jeu de données à partir des données dans les cellules mappées et lie le contrôle à ce jeu de données. La propriété de liaison de données par défaut de la <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Si les données dans le jeu de données liées sont mis à jour via un mécanisme quelconque, le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle reflète les modifications.  
  
## <a name="formatting"></a>Mise en forme  
 Vous pouvez appliquer la même mise en forme à un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle que vous pouvez appliquer à un <xref:Microsoft.Office.Interop.Excel.Range>. Cela inclut les bordures, les polices, le format de nombre et les styles.  
  
## <a name="events"></a>Événements  
 Les événements disponibles pour le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle sont :  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Voir aussi  
 [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  