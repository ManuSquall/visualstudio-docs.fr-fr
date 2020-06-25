---
title: Filtrer et trier des données dans une application Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c420896a883146cf60de414100fc41080220e36
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282382"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms

Vous filtrez les données en affectant <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété une expression de chaîne qui retourne les enregistrements souhaités.

Vous triez les données en définissant la <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété sur le nom de la colonne sur laquelle vous souhaitez effectuer le tri ; ajouter pour effectuer un `DESC` tri dans l’ordre décroissant ou pour effectuer un tri `ASC` dans l’ordre croissant.

> [!NOTE]
> Si votre application n’utilise pas de <xref:System.Windows.Forms.BindingSource> composants, vous pouvez filtrer et trier les données à l’aide d' <xref:System.Data.DataView> objets. Pour plus d’informations, consultez les [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne les clients avec un `CompanyName` qui commence par « B » :

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Sort%2A> à la propriété la colonne sur laquelle vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur la `CompanyName` colonne dans l’ordre décroissant :

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
