---
title: "XMLNodes, contr&#244;le"
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
  - "XMLNodes (contrôle)"
  - "XMLNodes (contrôle), événements"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes, contr&#244;le
  **important** les informations présentées dans cette rubrique concernant Microsoft Word est présenté exclusivement pour l'avantage et l'utilisation des personnes et organisations qui se trouvent en dehors de les états\-unis et de ses territoires ou qui utilisent, ou de développer des programmes qui s'exécutent sur, les produits Microsoft Word qui ont été autorisés par Microsoft avant janvier 2010, lorsque Microsoft a supprimé une implémentation de fonctionnalités spécifique liée à une personnalisée XML Microsoft Word.  Ces informations liées à Microsoft Word ne peuvent pas être lues ou utilisées par des individus ou des organisations se trouvant aux États\-Unis ou dans ses territoires qui utilisent, ou développent des programmes exécutés avec, des produits Microsoft Word dont la licence Microsoft est postérieure à janvier 2010 ; ces produits n'auront pas le même comportement que ceux dont la licence est antérieure à cette date ou ceux qui ont été achetés ou ont bénéficié d'une licence d'utilisation en dehors des États\-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> est une collection d'objets de nœud XML mappés qui expose des événements.  Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> est créé uniquement lorsqu'un élément de schéma répétitif est mappé à un document Microsoft Office Word.  Si l'élément répétitif contient des éléments enfants, chacun des éléments enfants est également créé en tant que contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
 Une fois que Visual Studio a créé la collection de nœuds XML, vous pouvez effectuer des programmations directement sur ce contrôle sans devoir parcourir le modèle objet Word.  Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> peut uniquement être supprimé en supprimant le mappage d'élément dans le document.  
  
> [!NOTE]  
>  Si vous accédez à un élément enfant du contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> via la propriété <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>, un objet <xref:Microsoft.Office.Interop.Word.XMLNode> est retourné, plutôt qu'un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode>.  Pour plus d’informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Liaison de données au contrôle  
 Un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> ne prend pas en charge la liaison de données.  En effet, le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> ne dispose pas de fonctions de liaison de données complexes, et la liaison de données simple ne peut pas représenter des données répétitives.  
  
## Mise en forme  
 Toute mise en forme qui peut être appliquée à du texte dans le document peut être appliquée à un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Événements  
 Les événements disponibles pour le contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> sont les suivants :  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## Événements de comparaison  
 Vous pouvez capturer un événement lorsque l'utilisateur déplace son curseur à l'intérieur du contexte d'un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> particulier.  Par exemple, vous pouvez avoir un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> nommé `Customer` qui possède un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes> enfant nommé `Company`, et `Company` a deux contrôles <xref:Microsoft.Office.Tools.Word.XMLNodes> enfants nommés `CompanyName` et `CompanyRegion` comme suit :  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si vous souhaitez afficher un contrôle sur le volet Actions chaque fois que le curseur est déplacé dans le nœud `Company`, le fait que le curseur soit placé dans `CompanyName` ou `CompanyRegion` n'a pas d'importance car ils sont tous deux dans le contexte de `Company`.  Dans ce cas, vous pouvez écrire votre code dans l'événement <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> de `Company`.  
  
 Dans la plupart des cas, lorsque le curseur entre dans un contrôle <xref:Microsoft.Office.Tools.Word.XMLNodes>, les événements <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> et <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> sont déclenchés.  Le tableau ci\-dessous indique les différences entre ces événements.  
  
|Événement Select|Événement ContextEnter|  
|----------------------|----------------------------|  
|Se produit lorsque le curseur est placé à l'intérieur de l'un des nœuds de la collection <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Se produit lorsque le curseur est placé à l'intérieur de l'un des nœuds ou des nœuds descendants de la collection <xref:Microsoft.Office.Tools.Word.XMLNodes>, à partir d'une zone en dehors du contexte du nœud.  En d'autres termes, il est déclenché uniquement lorsque le contexte change et peut être déclenché pour plusieurs contrôles <xref:Microsoft.Office.Tools.Word.XMLNodes> imbriqués.|  
  
 Par exemple, lorsque vous déplacez le curseur situé en dehors de `Customer` dans `CompanyName`, les événements <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> pour `Customer`, `Company` et `CompanyName` sont déclenchés.  Si vous déplacez ensuite le curseur de `CompanyName` vers `CompanyRegion`, l'événement <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> est déclenché pour `CompanyRegion` uniquement, car le contexte est identique pour `Company` et `Customer`.  Votre document peut comporter plusieurs nœuds `Company`.  Si vous déplacez le curseur à partir du nœud `CompanyName` d'un nœud `Company` vers le nœud `CompanyName` d'un autre nœud `Company`, le contexte est le même. Par conséquent, seul l'événement <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> est déclenché.  
  
 Les mêmes différences existent entre les événements <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> et <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>.  
  
## Voir aussi  
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode, contrôle](../vsto/xmlnode-control.md)   
 [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  