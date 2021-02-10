---
title: XMLNode (contrôle)
description: Découvrez que le contrôle XMLNode est un objet de nœud XML mappé qui expose des événements et qui peut être lié à des données.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9e86bfbe7af122e2557178f5d70256903d0cc740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949712"
---
# <a name="xmlnode-control"></a>XMLNode (contrôle)
  **Important** Les informations fournies dans cette rubrique concernant Microsoft Word sont présentées exclusivement pour l’avantage et l’utilisation des personnes et des organisations situées en dehors du États-Unis et de ses territoires, ou qui utilisent ou développent des programmes qui s’exécutent sur les produits Microsoft Word qui étaient sous licence par Microsoft avant le 2010 du 1er janvier, lorsque Microsoft a supprimé une implémentation de fonctionnalités particulières liées au code XML personnalisé de Ces informations relatives à Microsoft Word peuvent ne pas être lues ou utilisées par des personnes ou des organisations du États-Unis ou de ses territoires qui utilisent ou développent des programmes qui s’exécutent sur, les produits Microsoft Word qui étaient sous licence par Microsoft après le 10 janvier 2010 ; ces produits ne se comportent pas de la même façon que les produits sous licence avant cette date ou achetés et sous licence pour une utilisation en dehors du États-Unis.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est un objet de nœud XML mappé qui expose des événements et peut être lié aux données. Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle est créé uniquement lorsqu’un élément de schéma non répétitif est mappé à un document Word Microsoft Office. Une fois que Visual Studio a créé le nœud XML, vous pouvez le programmer directement sans avoir à parcourir le modèle objet Word.

 Le <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle peut être supprimé uniquement en supprimant le mappage d’éléments dans Word.

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle prend en charge la liaison de données simple. Le nœud XML doit être lié à une source de données à l’aide de la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriété. Si les données du jeu de données lié sont mises à jour, le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> reflète les changements apportés.

## <a name="formatting"></a>Mise en forme
 La mise en forme qui peut être appliquée à un <xref:Microsoft.Office.Interop.Word.XMLNode> objet peut être appliquée à un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle. Cela comprend les polices, les styles de soulignement et les styles de caractères.

## <a name="events"></a>Événements
 Les événements suivants sont disponibles pour le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Comparer les événements
 Vous pouvez capturer un événement lorsque l’utilisateur déplace son curseur dans le contexte d’un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle particulier. Par exemple, vous pouvez avoir un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle nommé `Customer` qui a un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle enfant nommé `Company` , et qui `Company` a deux <xref:Microsoft.Office.Tools.Word.XMLNode> contrôles enfants nommés `CompanyName` et `CompanyRegion` comme suit :

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si vous souhaitez afficher un contrôle sur le volet Actions chaque fois que le curseur est déplacé dans le `Company` nœud, il n’est pas important de savoir si le curseur est placé dans `CompanyName` ou `CompanyRegion` parce qu’ils sont à la fois dans le contexte de `Company` . Dans ce cas, vous pouvez écrire votre code en <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> cas de `Company` .

 Dans la plupart des cas, lorsque le curseur entre dans un <xref:Microsoft.Office.Tools.Word.XMLNode> contrôle, les <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événements et sont déclenchés. Le tableau suivant montre les différences entre ces événements.

|Sélectionner un événement|Événement ContextEnter|
|------------------|------------------------|
|Se produit lorsque le curseur est placé à l’intérieur d’un <xref:Microsoft.Office.Tools.Word.XMLNode> .|Se produit lorsque le curseur est placé à l'intérieur d'un nœud <xref:Microsoft.Office.Tools.Word.XMLNode> ou de l'un de ses nœuds descendants, à partir d'une zone en dehors du contexte du nœud. En d’autres termes, elle est déclenchée uniquement lorsque le contexte change.|

 Par exemple, lorsque vous déplacez le curseur en dehors de `Customer` dans `CompanyName` , l' <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement pour `Customer` , `Company` et `CompanyName` est déclenché. Si vous déplacez ensuite le curseur de `CompanyName` vers `CompanyRegion` , seul l' <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> événement pour `CompanyRegion` est déclenché parce que vous êtes toujours dans le contexte de `Company` et `Customer` .

 Les mêmes différences existent entre l' <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> événement et l' <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> événement.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes, contrôle](../vsto/xmlnodes-control.md)
- [Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
