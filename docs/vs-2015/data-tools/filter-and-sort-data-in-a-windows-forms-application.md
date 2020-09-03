---
title: Filtrer et trier des données dans une application Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671645"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous filtrez les données en affectant <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété une expression de chaîne qui retourne les enregistrements souhaités.

 Vous triez les données en définissant la <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété sur le nom de la colonne sur laquelle vous souhaitez effectuer le tri ; ajouter `DESC` pour trier par ordre décroissant ou ajouter `ASC` pour trier dans l’ordre croissant.

> [!NOTE]
> Si votre application n’utilise pas de <xref:System.Windows.Forms.BindingSource> composants, vous pouvez filtrer et trier les données à l’aide d' <xref:System.Data.DataView> objets. Pour plus d’informations, consultez les [DataView](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne les clients avec un `CompanyName` qui commence par « B » :

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier des données à l’aide d’un composant BindingSource

- Affectez <xref:System.Windows.Forms.BindingSource.Sort%2A> à la propriété la colonne sur laquelle vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur la `CompanyName` colonne dans l’ordre décroissant :

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
