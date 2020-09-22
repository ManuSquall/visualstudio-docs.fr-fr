---
title: XMLNodes (contrôle)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ad16165924a33a25dab2b1cfb49a0a7bbfe0875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840188"
---
# <a name="xmlnodes-control"></a>XMLNodes (contrôle)
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est une collection d’objets de nœud XML mappés qui expose des événements. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est créé uniquement lorsqu’un élément de schéma répétitif est mappé à un document Word Microsoft Office. Si l’élément répétitif contient des éléments enfants, chacun des éléments enfants est également créé en tant que <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.

 Une fois que Visual Studio a créé la collection de nœuds XML, vous pouvez programmer directement par rapport au contrôle sans avoir à parcourir le modèle objet Word. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle peut être supprimé uniquement en supprimant le mappage d’élément du document.

> [!NOTE]
> Si vous accédez à un élément enfant du <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle par le biais de la <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propriété, il retourne un <xref:Microsoft.Office.Interop.Word.XMLNode> objet plutôt qu’un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle ne prend pas en charge la liaison de données. Cela est dû au fait que le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle n’a pas de fonctionnalités de liaison de données complexes et que la liaison de données simple ne peut pas représenter des données répétées.

## <a name="formatting"></a>Mise en forme
 Toute mise en forme qui peut être appliquée à du texte dans le document peut être appliquée à un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.

## <a name="events"></a>Événements
 Les événements disponibles pour le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle sont les suivants :

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Comparer les événements
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle particulier. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle nommé `Customer` qui a un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle enfant nommé `Company` , et qui `Company` a deux <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles enfants nommés `CompanyName` et `CompanyRegion` comme suit :

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si vous souhaitez afficher un contrôle sur le volet Actions chaque fois que le curseur est déplacé dans le `Company` nœud, il n’est pas important de savoir si le curseur est placé dans `CompanyName` ou `CompanyRegion` parce qu’ils sont à la fois dans le contexte de `Company` . Dans ce cas, vous pouvez écrire votre code en <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> cas de `Company` .

 Dans la plupart des cas, lorsque le curseur entre dans un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle, les <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événements et sont déclenchés. Le tableau suivant présente les différences entre ces événements.

|Sélectionner un événement|Événement ContextEnter|
|------------------|------------------------|
|Se produit lorsque le curseur est placé à l'intérieur de l'un des nœuds de la collection <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Se produit lorsque le curseur est placé à l'intérieur de l'un des nœuds ou des nœuds descendants de la collection <xref:Microsoft.Office.Tools.Word.XMLNodes>, à partir d'une zone en dehors du contexte du nœud. En d’autres termes, elle est déclenchée uniquement lorsque le contexte change et peut être déclenchée pour plusieurs <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles imbriqués.|

 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName` , les <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événements pour `Customer` , `Company` et `CompanyName` sont déclenchés. Si vous déplacez ensuite le curseur de `CompanyName` vers `CompanyRegion` , l' <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événement uniquement pour `CompanyRegion` est déclenché, car le contexte est le même pour `Company` et `Customer` . Vous pouvez avoir plusieurs `Company` nœuds dans votre document. Si vous déplacez le curseur du `CompanyName` nœud d’un `Company` vers le `CompanyName` nœud d’un autre `Company` , le contexte est le même, donc seul l' <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> événement est déclenché.

 Les mêmes différences existent entre l' <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> événement et l' <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> événement.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode, contrôle](../vsto/xmlnode-control.md)
- [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
