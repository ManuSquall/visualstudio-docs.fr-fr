---
title: XMLNode (contrôle)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f83d829ac5067d751cc035ac83c0fb3397178658
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927439"
---
# <a name="xmlnode-control"></a>XMLNode (contrôle)
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présentée exclusivement pour le bénéfice et l’utilisation des individus et les organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui utilisent ou développement les programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft avant janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liés à XML personnalisé à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas être lues ou utilisées par les individus ou organisations dans les États-Unis ou dans ses territoires qui sont à l’aide d’ou de développer des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et concédés sous licence pour une utilisation en dehors des États-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est un objet de nœud XML mappé qui expose des événements et peut être lié aux données. Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est créé uniquement lorsqu’un élément de schéma non répétitif est mappé à un document Microsoft Office Word. Une fois que Visual Studio crée le nœud XML, vous pouvez le programmer directement, sans devoir parcourir le modèle objet Word.  
  
 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle peut être supprimé uniquement en supprimant le mappage d’élément dans Word.  
  
## <a name="bind-data-to-the-control"></a>Lier des données au contrôle  
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle prend en charge la liaison de données simple. Le nœud XML doit être lié à une source de données à l’aide de la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriété. Si les données du jeu de données lié sont mises à jour, le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> reflète les changements apportés.  
  
## <a name="formatting"></a>Mise en forme  
 Mise en forme qui peut être appliqué à un <xref:Microsoft.Office.Interop.Word.XMLNode> objet peut être appliqué à un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Cela inclut les polices, des styles de soulignement et des styles de caractère.  
  
## <a name="events"></a>Événements  
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
  
## <a name="compare-events"></a>Comparer des événements  
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un particulier <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle nommé `Customer` qui a un enfant <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle nommé `Company`, et `Company` a deux enfants <xref:Microsoft.Office.Tools.Word.XMLNode> contrôles nommés `CompanyName` et `CompanyRegion` comme suit :  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si vous souhaitez afficher un contrôle sur le volet actions chaque fois que le curseur est déplacé dans le `Company` nœud, il importe peu que le curseur est placé dans `CompanyName` ou `CompanyRegion` , car elles sont toutes deux dans le contexte de `Company`. Dans ce cas, vous pouvez écrire votre code le <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement de `Company`.  
  
 Dans la plupart des cas, lorsque le curseur passe un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôler, à la fois le <xref:Microsoft.Office.Tools.Word.XMLNode.Select> et <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> sont déclenchés. Le tableau suivant montre les différences entre ces événements.  
  
|Sélectionnez l’événement|Événement ContextEnter|  
|------------------|------------------------|  
|Se produit lorsque le curseur est placé à l’intérieur d’un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Se produit lorsque le curseur est placé à l’intérieur d’un <xref:Microsoft.Office.Tools.Word.XMLNode> ou l’un de ses nœuds descendants, à partir d’une zone en dehors du contexte du nœud. En d’autres termes, il est déclenché uniquement lorsque le contexte change.|  
  
 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName`, le <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement pour `Customer`, `Company`, et `CompanyName` est déclenché. Si vous déplacez ensuite le curseur de `CompanyName` à `CompanyRegion`, seule la <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement pour `CompanyRegion` est déclenché, car vous êtes toujours dans le contexte des deux `Company` et `Customer`.  
  
 Les mêmes différences existent entre les <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> événement et <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes, contrôle](../vsto/xmlnodes-control.md)   
 [Guide pratique pour Ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Guide pratique pour Mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
