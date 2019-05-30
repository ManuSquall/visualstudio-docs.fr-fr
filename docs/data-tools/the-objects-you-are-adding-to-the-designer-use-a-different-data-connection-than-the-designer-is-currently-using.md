---
title: Objets ajoutés au concepteur utilisent une connexion de données différents
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c85e0c17eeb4cfbd786faac338c8b908c5a7f363
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260936"
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

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
