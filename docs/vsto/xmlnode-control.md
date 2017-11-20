---
title: "XMLNode (contrôle) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: XMLNode control
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c35726314dc679289554e24d4150da4294cf8a0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnode-control"></a>XMLNode, contrôle
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présenté exclusivement pour le bénéfice et l’utilisation des personnes et des organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui sont à l’aide d’ou de développement programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft avant de janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liées à XML personnalisées à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas lire ou utilisées par des individus ou organisations États-Unis ou dans ses territoires qui utilisent, ou développent des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et une licence d’utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est un objet de nœud XML mappé qui expose des événements et peut être lié aux données. Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est créé uniquement lorsqu’un élément de schéma non répétitif est mappé à un document Microsoft Office Word. Une fois que Visual Studio crée le nœud XML, vous pouvez le programmer directement sans avoir à parcourir le modèle objet Word.  
  
 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle peut être supprimé uniquement en supprimant le mappage d’élément dans Word.  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle prend en charge la liaison de données simple. Le nœud XML doit être lié à une source de données à l’aide de la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriété. Si les données du DataSet lié sont mis à jour, la <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle reflète les modifications.  
  
## <a name="formatting"></a>Mise en forme  
 Mise en forme qui peut être appliqué à un <xref:Microsoft.Office.Interop.Word.XMLNode> objet peut être appliqué à un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Cela inclut les polices, des styles de soulignement et des styles de caractère.  
  
## <a name="events"></a>Événements  
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> :  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Événements de comparaison  
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un particulier <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle nommé `Customer` qui a un enfant <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle nommé `Company`, et `Company` a deux enfants <xref:Microsoft.Office.Tools.Word.XMLNode> contrôles nommés `CompanyName` et `CompanyRegion` comme suit :  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si vous souhaitez afficher un contrôle dans le volet actions chaque fois que le curseur est déplacé dans le `Company` nœud, il importe peu que le curseur est placé dans `CompanyName` ou `CompanyRegion` car ils sont tous deux dans le contexte de `Company`. Dans ce cas, vous pouvez écrire votre code dans le <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> l’événement de `Company`.  
  
 Dans la plupart des cas, lorsque le curseur passe un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôler, à la fois le <xref:Microsoft.Office.Tools.Word.XMLNode.Select> et <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> sont déclenchés. Le tableau suivant indique les différences entre ces événements.  
  
|Sélectionnez un événement|Événement ContextEnter|  
|------------------|------------------------|  
|Se produit lorsque le curseur est placé à l’intérieur d’un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Se produit lorsque le curseur est placé à l’intérieur d’un <xref:Microsoft.Office.Tools.Word.XMLNode> ou l’un de ses nœuds descendants, à partir d’une zone en dehors du contexte du nœud. En d’autres termes, il est déclenché uniquement lorsque le contexte change.|  
  
 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName`, le <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement `Customer`, `Company`, et `CompanyName` est déclenché. Si vous déplacez ensuite le curseur à partir de `CompanyName` à `CompanyRegion`, seule la <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement pour `CompanyRegion` est déclenché, car vous êtes encore dans le contexte des deux `Company` et `Customer`.  
  
 Les mêmes différences existent entre les <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> événement et <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes (contrôle)](../vsto/xmlnodes-control.md)   
 [Comment : ajouter des contrôles XMLNode à des Documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Comment : mapper des schémas à des Documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  