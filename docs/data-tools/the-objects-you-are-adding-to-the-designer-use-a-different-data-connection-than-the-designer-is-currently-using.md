---
title: Les objets que vous ajoutez au concepteur utilisent une connexion de données différente de celle utilisée actuellement par le concepteur
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e0864ec07250ed5886f864d4233aeb902ecf5ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565620"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Les objets que vous ajoutez au concepteur utilisent une connexion de données autre que le Concepteur

Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur en cours d'utilisation. Voulez-vous remplacer la connexion utilisée par le concepteur ?

Lorsque vous ajoutez des éléments à la **concepteur objet/relationnel** (**Concepteur O/R**), tous les éléments utilisent une seule connexion de données partagée. (L'aire de conception représente le <xref:System.Data.Linq.DataContext> qui utilise une connexion unique pour tous les objets sur l'aire.) Si vous ajoutez un objet au concepteur qui utilise une connexion de données différente de la connexion de données qui est actuellement utilisée par le concepteur, ce message apparaît. Pour résoudre cette erreur, vous pouvez maintenir la connexion existante. Dans ce cas, l'objet sélectionné n'est pas ajouté. Vous pouvez également choisir d’ajouter l’objet et de réinitialiser la connexion <xref:System.Data.Linq.DataContext> à la nouvelle connexion.

## <a name="connection-options"></a>Options de connexion

- Pour remplacer la connexion existante avec la connexion utilisée par l’objet sélectionné, cliquez sur **Oui**.

   L’objet sélectionné est ajouté à la **Concepteur O/R**et le *DataContext.Connection* est définie sur la nouvelle connexion.

   > [!NOTE]
   > Si vous cliquez sur **Oui**, classes d’entité toutes sur le **Concepteur O/R** sont mappées à la nouvelle connexion.

- Pour continuer à utiliser la connexion existante et annuler l’ajout de l’objet sélectionné, cliquez sur **non**.

   L'action est annulée. *DataContext.Connection* conserve la connexion existante.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
