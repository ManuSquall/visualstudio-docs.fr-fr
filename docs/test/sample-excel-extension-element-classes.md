---
title: "Exemple d&#39;extension Excel&#160;: classes d&#39;&#233;l&#233;ments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Exemple d&#39;extension Excel&#160;: classes d&#39;&#233;l&#233;ments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'extension utilise des classes qui sont dérivées de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> et qui représentent le contrôle Worksheet et contrôle Cell dans [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 L'élément de base de cette extension est l'`ExcelElement`.  La classe `ExcelWorksheetElement` et la classe `ExcelCellElement` hérite de cet élément  
  
## Élément et classes ElementInformation  
 L'`Element` est la classe de base pour tous les éléments de l'interface utilisateur pour l'extension Excel, et il hérite de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>.  `ElementInformation` est la classe de base des classes d'informations de l'élément dans l'exemple, et n'a pas de membres.  
  
#### Propriétés et méthodes simples  
 Ces membres retournent des valeurs simples, telles que la valeur de la propriété `Name` ou la valeur de la propriété `ClassName`, et le code est clair et facile à lire.  Certaines valeurs sont retournées à l'aide de la classe `Utility`, traitée ultérieurement.  D'autres retournent `null` parce qu'elles ne sont pas significatives dans cette exemple d'extension.  Deux membres sont plus intéressants que les autres : la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> et la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### Propriété QueryId  
 Cette propriété retourne une condition composée de paires nom\-valeur de la propriété qui identifient uniquement le contrôle pendant la lecture.  Pour chaque classe de contrôle dérivée, le développeur doit remplacer cette propriété pour retourner un objet <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> que l'infrastructure peut utiliser pour rechercher le contrôle dans l'interface utilisateur.  
  
#### Méthode CacheProperties  
 Cette méthode est appelée par l'infrastructure des tests pendant le processus d'enregistrement pour indiquer à l'élément d'enregistrer un instantané des propriétés importantes.  Cela permet de rendre les propriétés disponibles même quand le contrôle d'IU réel n'est plus à l'écran.  
  
## Classes WorksheetElement et WorksheetInformation  
 La classe `WorksheetElement` représente une feuille de calcul Excel dans l'infrastructure de tests et hérite de la classe de base `Element`.  Trois propriétés sont remplacées pour fournir des informations spécifiques sur l'objet feuille de calcul Excel : <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> et <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 L'<xref:System.Runtime.InteropServices.ComVisibleAttribute> est également appliqué à cette classe pour le rendre visible par COM.  
  
 La classe `WorksheetInformation` représente les informations sur une feuille de calcul Excel.  Il possède un seul membre, la propriété `SheetName`, qui est suffisante pour cet exemple.  
  
## Classes CellElement and CellInformation  
 La classe `CellElement` représente une cellule Excel et hérite de la classe de base `Element`.  Le seul membre remplacé est la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> qui retourne un <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> qui utilise les propriétés `RowIndex` et `ColumnIndex` pour identifier la cellule.  
  
## Classes Utilities et ExcelUtilities  
 La classe `ExcelUtilities` interne fournit certaines valeurs constantes, telles que le nom de la technologie, et une méthode qui détermine si le handle de fenêtre fourni représente une feuille de calcul Excel.  
  
 La classe `Utilities` possède des méthodes d'assistance qui retournent diverses informations sur l'interface utilisateur.  Certaines méthodes utilisent des appels directs dans les DLL des système externes, telles que **USER32.DLL** et **OLEACC.DLL**, pour obtenir des handles de fenêtre de l'interface utilisateur**.**  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)