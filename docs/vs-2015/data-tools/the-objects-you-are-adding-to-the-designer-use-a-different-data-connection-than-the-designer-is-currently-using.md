---
title: Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur est actuellement à l’aide de | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 960d3123c45e44b2b1cdc64b896b15b82e655bb2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102836"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Les objets que vous ajoutez au concepteur utilisent une connexion de données différente de celle utilisée actuellement par le concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur en cours d'utilisation. Voulez-vous remplacer la connexion utilisée par le concepteur ?  
  
 Lorsque vous ajoutez des éléments à la [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), tous les éléments utilisent une seule connexion de données partagée. (L'aire de conception représente le <xref:System.Data.Linq.DataContext> qui utilise une connexion unique pour tous les objets sur l'aire.) Si vous ajoutez un objet au concepteur qui utilise une connexion de données différente de la connexion de données qui est actuellement utilisée par le concepteur, ce message apparaît. Pour résoudre cette erreur, vous pouvez maintenir la connexion existante. Dans ce cas, l'objet sélectionné n'est pas ajouté. Vous pouvez également choisir d’ajouter l’objet et de réinitialiser la connexion <xref:System.Data.Linq.DataContext> à la nouvelle connexion.  
  
> [!NOTE]
>  Si vous cliquez sur **Oui**, classes d’entité toutes sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sont mappées à la nouvelle connexion.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Pour remplacer la connexion existante par la connexion qu'utilise l'objet sélectionné  
  
- Cliquez sur **Oui**.  
  
     L'objet sélectionné est ajouté au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] et DataContext.Connection a pour valeur la nouvelle connexion.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Pour continuer d'utiliser la connexion existante et annuler l'ajout de l'objet sélectionné  
  
- Cliquez sur **Non**.  
  
     L'action est annulée. DataContext.Connection conserve la connexion existante.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   