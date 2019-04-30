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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421534"
---
# <a name="xmlnodes-control"></a>XMLNodes (contrôle)
  **Important** les informations mentionnées dans cette rubrique concernant Microsoft Word sont présentée exclusivement pour le bénéfice et l’utilisation des individus et les organisations qui se trouvent en dehors des États-Unis et ses territoires ou qui utilisent ou développement les programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft avant janvier 2010, lorsque Microsoft supprimé une implémentation de fonctionnalités spécifiques liés à XML personnalisé à partir de Microsoft Word. Ces informations concernant Microsoft Word ne peuvent pas être lues ou utilisées par les individus ou organisations dans les États-Unis ou dans ses territoires qui sont à l’aide d’ou de développer des programmes qui s’exécutent sur des produits de Microsoft Word qui ont été concédés sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne comportent pas le même que les produits sous licence avant cette date ou acheté et concédés sous licence pour une utilisation en dehors des États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est une collection d’objets de nœud XML mappés qui expose des événements. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle est créé uniquement lorsqu’un élément de schéma répétitif est mappé à un document Microsoft Office Word. Si l’élément répétitif contienne des éléments enfants, chacun des éléments enfants est également créé comme un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.

 Une fois que Visual Studio crée la collection de nœuds XML, vous pouvez programmer le contrôle directement, sans devoir parcourir le modèle objet Word. Le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle peut être supprimé uniquement en supprimant le mappage d’élément à partir du document.

> [!NOTE]
> Si vous accédez à un élément enfant de le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôler via le <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propriété, elle retourne un <xref:Microsoft.Office.Interop.Word.XMLNode> objet au lieu d’un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle ne prend pas en charge la liaison de données. Il s’agit, car le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle n’a pas de fonctionnalités de liaison de données complexe, et liaison de données simple ne peut pas représenter des données duplicables.

## <a name="formatting"></a>Mise en forme
 Mise en forme qui peut être appliqué au texte dans le document peut être appliqué à un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle.

## <a name="events"></a>Événements
 Les événements disponibles pour le <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle sont :

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Comparer des événements
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un particulier <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle nommé `Customer` qui a un enfant <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôle nommé `Company`, et `Company` a deux enfants <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles nommés `CompanyName` et `CompanyRegion` comme suit :

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si vous souhaitez afficher un contrôle sur le volet actions chaque fois que le curseur est déplacé dans le `Company` nœud, il importe peu que le curseur est placé dans `CompanyName` ou `CompanyRegion` , car elles sont toutes deux dans le contexte de `Company`. Dans ce cas, vous pouvez écrire votre code le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événement de `Company`.

 Dans la plupart des cas, lorsque le curseur passe un <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôler, à la fois le <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> et <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> sont déclenchés. Le tableau suivant présente les différences entre ces événements.

|Sélectionnez l’événement|Événement ContextEnter|
|------------------|------------------------|
|Se produit lorsque le curseur est placé à l’intérieur d’un des nœuds de la <xref:Microsoft.Office.Tools.Word.XMLNodes> collection.|Se produit lorsque le curseur est placé dans l’un des nœuds ou des nœuds descendants de le <xref:Microsoft.Office.Tools.Word.XMLNodes> collection, à partir d’une zone en dehors du contexte du nœud. En d’autres termes, il est déclenché uniquement lorsque le contexte change et peut être déclenché pour plusieurs imbriqués <xref:Microsoft.Office.Tools.Word.XMLNodes> contrôles.|

 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName`, le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événements pour `Customer`, `Company`, et `CompanyName` sont déclenchés. Si vous déplacez ensuite le curseur de `CompanyName` à `CompanyRegion`, le <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> événement uniquement pour `CompanyRegion` est déclenché, car le contexte est le même pour les deux `Company` et `Customer`. Vous pouvez avoir plusieurs `Company` nœuds dans votre document. Si vous déplacez le curseur à partir de la `CompanyName` nœud d’un `Company` à la `CompanyName` nœud d’un autre `Company`, le contexte est identique, afin que seuls les <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> événement est déclenché.

 Les mêmes différences existent entre les <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> événement et le <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> événement.

## <a name="see-also"></a>Voir aussi
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode, contrôle](../vsto/xmlnode-control.md)
- [Guide pratique pour Ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Guide pratique pour Mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
