---
title: Les objets que vous ajoutez au concepteur utilisent une connexion de données différente de celle utilisée actuellement par le concepteur
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33a6083fb9e52ebdafbc827fc19666c1df9a3f7e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924514"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Les objets que vous ajoutez au concepteur utilisent une connexion de données autre que le Concepteur

Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur en cours d'utilisation. Voulez-vous remplacer la connexion utilisée par le concepteur ?

Lorsque vous ajoutez des éléments à la [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), tous les éléments utilisent une connexion de données partagée. (L'aire de conception représente le <xref:System.Data.Linq.DataContext> qui utilise une connexion unique pour tous les objets sur l'aire.) Si vous ajoutez un objet au concepteur qui utilise une connexion de données différente de la connexion de données qui est actuellement utilisée par le concepteur, ce message apparaît. Pour résoudre cette erreur, vous pouvez maintenir la connexion existante. Dans ce cas, l'objet sélectionné n'est pas ajouté. Vous pouvez également ajouter l’objet et de réinitialiser le <xref:System.Data.Linq.DataContext> la connexion à la nouvelle connexion.

> [!NOTE]
> Si vous cliquez sur **Oui**, classes d’entité toutes sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sont mappées à la nouvelle connexion.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Pour remplacer la connexion existante par la connexion qu'utilise l'objet sélectionné

- Cliquez sur **Oui**.

    L'objet sélectionné est ajouté au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et DataContext.Connection a pour valeur la nouvelle connexion.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Pour continuer d'utiliser la connexion existante et annuler l'ajout de l'objet sélectionné

- Cliquez sur **Non**.

    L'action est annulée. DataContext.Connection conserve la connexion existante.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
