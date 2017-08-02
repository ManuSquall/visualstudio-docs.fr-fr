---
title: "XmlMappedRange, contr&#244;le"
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
  - "XMLMappedRange (contrôle)"
  - "XMLMappedRange (contrôle), liaison de données"
  - "XMLMappedRange (contrôle), événements"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange, contr&#244;le
  Le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est une plage créée uniquement lorsqu'un élément de schéma non répétitif est mappé sur une cellule dans Microsoft Office Excel.  Par exemple, lorsque l'attribut `maxOccurs` d'un élément de schéma est égal à 1.  Une fois que Visual Studio a créé la plage mappée en XML, vous pouvez effectuer des programmations directement sur cette plage sans devoir parcourir le modèle objet Excel.  Vous pouvez supprimer un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> dans Excel uniquement lorsque le mappage d'élément est supprimé.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![lien vers la vidéo](~/data-tools/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [Comment faire pour utiliser le mappage XML dans Excel ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## Liaison de données au contrôle  
 Un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> prend en charge la liaison à un seul champ de données \(liaison de données simple\).  Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut prendre en charge la liaison de données complexe et est automatiquement créé lorsqu'un élément de schéma répétitif est mappé à une cellule.  Pour plus d’informations, consultez [ListObject, contrôle](../vsto/listobject-control.md).  
  
 Le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est lié à une source de données à l'aide de la propriété <xref:System.Windows.Forms.Control.DataBindings%2A>.  Lorsqu'un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est ajouté à une cellule de feuille de calcul, Visual Studio génère automatiquement un groupe de données à partir des données des cellules mappées et lie le contrôle à ce groupe.  La propriété de liaison de données par défaut de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Si les données du groupe de données lié sont mises à jour par le biais d'un mécanisme quelconque, ces modifications sont répercutées dans le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  
  
## Mise en forme  
 Vous pouvez appliquer la même mise en forme à un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> qu'à un contrôle <xref:Microsoft.Office.Interop.Excel.Range>.  Cela inclut les bordures, les polices, le format de nombre et les styles.  
  
## Événements  
 Les événements disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> sont les suivants :  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## Voir aussi  
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  