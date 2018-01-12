---
title: "XMLNodes (contrôle) | Documents Microsoft"
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
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1a3759070d406e721a12e01950e0e99cea40d1fc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnodes-control"></a>XMLNodes, contrôle
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présenté exclusivement pour le bénéfice et l’utilisation des personnes et des organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui sont à l’aide d’ou de développement programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft avant de janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liées à XML personnalisées à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas lire ou utilisées par des individus ou organisations États-Unis ou dans ses territoires qui utilisent, ou développent des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédé sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et une licence d’utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est une collection d’objets de nœud XML mappés qui expose des événements. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est créé uniquement lorsqu’un élément de schéma répétitif est mappé à un document Microsoft Office Word. Si l’élément répétitif contienne des éléments enfants, chacun des éléments enfants est également créé comme un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.  
  
 Une fois que Visual Studio crée la collection de nœuds XML, vous pouvez programmer le contrôle directement sans avoir à parcourir le modèle objet Word. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle peut être supprimé uniquement en supprimant le mappage d’élément à partir du document.  
  
> [!NOTE]  
>  Si vous accédez à un élément enfant de le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôler via le <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propriété, elle retourne un <xref:Microsoft.Office.Interop.Word.XMLNode> objet plutôt qu’un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Pour plus d'informations, consultez [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle ne prend pas en charge la liaison de données. C’est parce que le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle n’a pas de fonctionnalités de liaison de données complexe, et liaison de données simple ne peut pas représenter répéter des données.  
  
## <a name="formatting"></a>Mise en forme  
 Mise en forme qui peut être appliquée au texte dans le document peut être appliquée à un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.  
  
## <a name="events"></a>Événements  
 Les événements disponibles pour le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle sont :  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Événements de comparaison  
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un particulier <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle nommé `Customer` qui a un enfant <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle nommé `Company`, et `Company` a deux enfants <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles nommés `CompanyName` et `CompanyRegion` comme suit :  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si vous souhaitez afficher un contrôle dans le volet actions chaque fois que le curseur est déplacé dans le `Company` nœud, il importe peu que le curseur est placé dans `CompanyName` ou `CompanyRegion` car ils sont tous deux dans le contexte de `Company`. Dans ce cas, vous pouvez écrire votre code dans le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> l’événement de `Company`.  
  
 Dans la plupart des cas, lorsque le curseur passe un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôler, à la fois le <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> et <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> sont déclenchés. Le tableau suivant montre les différences entre ces événements.  
  
|Sélectionnez un événement|Événement ContextEnter|  
|------------------|------------------------|  
|Se produit lorsque le curseur est placé à l’intérieur d’un des nœuds de la <xref:Microsoft.Office.Tools.Word.XMLNodes> collection.|Se produit lorsque le curseur est placé à l’intérieur d’un des nœuds ou des nœuds descendants de le <xref:Microsoft.Office.Tools.Word.XMLNodes> collection, à partir d’une zone en dehors du contexte du nœud. En d’autres termes, il est déclenché uniquement lorsque le contexte change et peut être déclenché pour plusieurs imbriqués <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles.|  
  
 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName`, le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événements pour `Customer`, `Company`, et `CompanyName` sont déclenchés. Si vous déplacez ensuite le curseur à partir de `CompanyName` à `CompanyRegion`, le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événement uniquement pour `CompanyRegion` est déclenché, car le contexte est le même pour les deux `Company` et `Customer`. Vous pouvez avoir plusieurs `Company` nœuds dans votre document. Si vous déplacez le curseur à partir de la `CompanyName` nœud d’un `Company` à la `CompanyName` nœud d’un autre `Company`, le contexte est le même, seulement le <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> événement est déclenché.  
  
 Les mêmes différences existent entre les <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> événement et le <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode (contrôle)](../vsto/xmlnode-control.md)   
 [Comment : ajouter des contrôles XMLNodes à des Documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Comment : mapper des schémas à des Documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  