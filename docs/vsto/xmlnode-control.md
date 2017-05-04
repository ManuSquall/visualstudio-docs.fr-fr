---
title: "XMLNode, contr&#244;le | Microsoft Docs"
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
  - "XMLNode (contrôle)"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode, contr&#244;le
  **important** les informations présentées dans cette rubrique concernant Microsoft Word est présenté exclusivement pour l'avantage et l'utilisation des personnes et organisations qui se trouvent en dehors de les états\-unis et de ses territoires ou qui utilisent, ou de développer des programmes qui s'exécutent sur, les produits Microsoft Word qui ont été autorisés par Microsoft avant janvier 2010, lorsque Microsoft a supprimé une implémentation de fonctionnalités spécifique liée à une personnalisée XML Microsoft Word.  Ces informations liées à Microsoft Word ne peuvent pas être lues ou utilisées par des individus ou des organisations se trouvant aux États\-Unis ou dans ses territoires qui utilisent, ou développent des programmes exécutés avec, des produits Microsoft Word dont la licence Microsoft est postérieure à janvier 2010 ; ces produits n'auront pas le même comportement que ceux dont la licence est antérieure à cette date ou ceux qui ont été achetés ou ont bénéficié d'une licence d'utilisation en dehors des États\-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> est un objet de nœud XML mappé qui expose des événements et peut être lié aux données.  Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> est créé uniquement lorsqu'un élément de schéma non répétitif est mappé à un document Microsoft Office Word.  Une fois que Visual Studio a créé le nœud XML, vous pouvez effectuer des programmations directement sur cette plage sans devoir parcourir le modèle objet Word.  
  
 Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> ne peut être supprimé qu'en retirant le mappage d'élément dans Word.  
  
## Liaison de données au contrôle  
 Un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> prend en charge la liaison de données simple.  Le nœud XML doit être lié à une source de données à l'aide de la propriété <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>.  Si les données du groupe de données lié sont mises à jour, les modifications sont répercutées dans le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode>.  
  
## Mise en forme  
 Une mise en forme qui peut être appliquée à un objet <xref:Microsoft.Office.Interop.Word.XMLNode> peut être appliquée à un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode>.  Cela inclut les polices, les styles de soulignement et les styles de caractères.  
  
## Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> :  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## Événements de comparaison  
 Vous pouvez capturer un événement lorsque l'utilisateur déplace son curseur à l'intérieur du contexte d'un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> particulier.  Par exemple, vous pouvez avoir un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> nommé `Customer` qui possède un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> enfant nommé `Company`, et `Company` a deux contrôles <xref:Microsoft.Office.Tools.Word.XMLNode> enfants nommés `CompanyName` et `CompanyRegion` comme suit :  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si vous souhaitez afficher un contrôle sur le volet Actions chaque fois que le curseur est déplacé dans le nœud `Company`, le fait que le curseur soit placé dans `CompanyName` ou `CompanyRegion` n'a pas d'importance car ils sont tous deux dans le contexte de `Company`.  Dans ce cas, vous pouvez écrire votre code dans l'événement <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> de `Company`.  
  
 Dans la plupart des cas, lorsque le curseur entre dans un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode>, les événements <xref:Microsoft.Office.Tools.Word.XMLNode.Select> et <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> sont déclenchés.  Le tableau suivant montre les différences entre ces événements.  
  
|Événement de sélection|Événement ContextEnter|  
|----------------------------|----------------------------|  
|Se produit lorsque le curseur est placé à l'intérieur d'un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Se produit lorsque le curseur est placé à l'intérieur d'un nœud <xref:Microsoft.Office.Tools.Word.XMLNode> ou de l'un de ses nœuds descendants, à partir d'une zone en dehors du contexte du nœud.  En d'autres termes, il est déclenché uniquement lorsque le contexte change.|  
  
 Par exemple, lorsque vous déplacez le curseur situé en dehors de `Customer` dans `CompanyName`, l'événement <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> pour `Customer`, `Company` et `CompanyName` est déclenché.  Si vous déplacez ensuite le curseur de `CompanyName` vers `CompanyRegion`, seul l'événement <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> pour `CompanyRegion` est déclenché car vous êtes encore dans le contexte de `Company` et `Customer`.  
  
 Les mêmes différences existent entre l'événement <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> et l'événement <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>.  
  
## Voir aussi  
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes, contrôle](../vsto/xmlnodes-control.md)   
 [Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  