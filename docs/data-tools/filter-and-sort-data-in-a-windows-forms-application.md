---
title: Filtrer et trier des données dans une application Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ed61f8e1ee864cc07132ae003dc0238884d370ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997921"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms

Filtrer les données en définissant le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété à une expression de chaîne qui retourne les enregistrements souhaités.

Trier les données en définissant le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété le nom de colonne sur laquelle vous souhaitez effectuer le tri ; ajoutez `DESC` à trier par ordre décroissant, ou d’ajouter `ASC` à trier par ordre croissant.

> [!NOTE]
> Si votre application n’utilise pas <xref:System.Windows.Forms.BindingSource> composants, vous pouvez filtrer et trier des données à l’aide de <xref:System.Data.DataView> objets. Pour plus d’informations, consultez [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer les données à l’aide d’un composant BindingSource

-   Définir le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété à l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne des clients avec un `CompanyName` qui commence par « B » :

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier les données à l’aide d’un composant BindingSource

-   Définir le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété à la colonne que vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur le `CompanyName` colonne dans l’ordre décroissant :

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)