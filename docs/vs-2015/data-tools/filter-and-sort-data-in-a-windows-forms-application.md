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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5592a488788c61af7ad6875de239fca62746857c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938540"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrer et trier des données dans une application Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Filtrer les données en définissant le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété à une expression de chaîne qui retourne les enregistrements souhaités.  
  
 Trier les données en définissant le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété le nom de colonne que vous souhaitez effectuer le tri ; ajouter `DESC` à trier par ordre décroissant, ou d’ajouter `ASC` à trier par ordre croissant.  
  
> [!NOTE]
>  Si votre application n’utilise pas <xref:System.Windows.Forms.BindingSource> composants, vous pouvez filtrer et trier des données à l’aide de <xref:System.Data.DataView> objets. Pour plus d’informations, consultez [DataViews](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Pour filtrer les données à l’aide d’un composant BindingSource  
  
-   Définir le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété à l’expression que vous souhaitez retourner. Par exemple, le code suivant retourne des clients avec un `CompanyName` qui commence par « B » :  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Pour trier les données à l’aide d’un composant BindingSource  
  
-   Définir le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété à la colonne que vous souhaitez effectuer le tri. Par exemple, le code suivant trie les clients sur le `CompanyName` colonne dans l’ordre décroissant :  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
