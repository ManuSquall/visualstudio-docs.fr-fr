---
title: "Propri&#233;t&#233;s dans les projets Office"
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
  - "Emplacement des assemblys de confiance (propriété)"
  - "CacheInDocument (propriété)"
  - "propriétés (développement Office dans Visual Studio)"
  - "Espace de noms de l'élément hôte (propriété)"
  - "projets Office (développement Office dans Visual Studio), propriétés"
  - "projets (développement Office dans Visual Studio), propriétés"
  - "Value2 (propriété)"
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Propri&#233;t&#233;s dans les projets Office
  Plusieurs propriétés importantes peuvent être définies pour les projets Office dans Visual Studio. Ces propriétés sont disponibles dans la fenêtre **Propriétés**.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Espace de noms de l'élément hôte  
 Utilisez la propriété **Espace de noms de l'élément hôte** pour modifier l'espace de noms des classes d'élément hôte \(par exemple, les classes `ThisAddIn`, `ThisWorkbook` ou `ThisDocument`\) dans les projets Visual C\#. Cette propriété s’affiche dans la fenêtre **Propriétés** quand vous sélectionnez le nœud de document dans un projet de niveau document \(ClasseurExcel1.xlsx ou DocumentWord1.docx, par exemple\) ou le nœud d’application dans un projet de complément VSTO \(Excel ou Word, par exemple\) dans l’**Explorateur de solutions**.  
  
 Quand vous créez un projet Office Visual C\#, un espace de noms basé sur le nom du projet est attribué aux éléments hôtes. Il est recommandé d'utiliser la propriété **Espace de noms de l'élément hôte** pour modifier l'espace de noms, plutôt que de modifier directement les fichiers de code. Quand vous utilisez cette propriété, l'espace de noms est modifié dans les fichiers de code générés \(masqués\), ainsi que dans les fichiers de code visibles.  
  
## CacheInDocument  
 La propriété **CacheInDocument** s'affiche dans la fenêtre **Propriétés** pour les projets de niveau document quand vous sélectionnez une instance de <xref:System.Data.DataSet> dans le concepteur Visual Studio. Seuls les membres publics peuvent être mis en cache. Vérifiez que la propriété **Modifiers** a la valeur **Public** si vous souhaitez mettre en cache <xref:System.Data.DataSet>.  
  
 Cette propriété accepte une valeur booléenne :  
  
-   Choisissez **true** pour mettre le dataset en cache dans le document.  
  
-   Choisissez **false** si vous ne voulez pas que le dataset soit mis en cache dans le document.  
  
 Pour plus d’informations sur la mise en cache de données, consultez [Données mises en cache dans des personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).  
  
## Value2  
 La propriété **Value2** est uniquement disponible pour les projets de modèle ou de classeur Excel. Elle s'affiche sous le nœud de propriété **Databindings** dans la fenêtre **Propriétés** quand vous sélectionnez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> dans le concepteur de feuilles de calcul.  
  
 Utilisez la propriété **Value2** dans la fenêtre **Propriétés** pour lier la propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> de <xref:Microsoft.Office.Tools.Excel.NamedRange> à un champ dans la source de données.  
  
## Voir aussi  
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)   
 [Événements dans les projets Office](../vsto/events-in-office-projects.md)  
  
  