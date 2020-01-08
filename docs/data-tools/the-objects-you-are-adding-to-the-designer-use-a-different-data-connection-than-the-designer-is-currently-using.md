---
title: Les objets ajoutés au concepteur utilisent une connexion de données différente
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9a3a2e00ccdee20fd374c52235ba648f89a0faa1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586157"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Les objets que vous ajoutez au concepteur utilisent une connexion de données différente de celle du concepteur.

Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur en cours d'utilisation. Voulez-vous remplacer la connexion utilisée par le concepteur ?

Lorsque vous ajoutez des éléments au **Concepteur Objet Relationnel** (**Concepteur O/R**), tous les éléments utilisent une connexion de données partagée. (L’aire de conception représente l' <xref:System.Data.Linq.DataContext>, qui utilise une seule connexion pour tous les objets sur l’aire.) Si vous ajoutez un objet au concepteur qui utilise une connexion de données différente de la connexion de données actuellement utilisée par le concepteur, ce message s’affiche. Pour résoudre cette erreur, vous pouvez maintenir la connexion existante. Dans ce cas, l'objet sélectionné n'est pas ajouté. Vous pouvez également choisir d’ajouter l’objet et de réinitialiser la connexion <xref:System.Data.Linq.DataContext> à la nouvelle connexion.

## <a name="connection-options"></a>Options de connexion

- Pour remplacer la connexion existante par la connexion utilisée par l’objet sélectionné, cliquez sur **Oui**.

   L’objet sélectionné est ajouté au **Concepteur O/R**, et la connexion *DataContext. Connection* est définie sur la nouvelle connexion.

   > [!NOTE]
   > Si vous cliquez sur **Oui**, toutes les classes d’entité sur le **Concepteur O/R** sont mappées à la nouvelle connexion.

- Pour continuer à utiliser la connexion existante et annuler l’ajout de l’objet sélectionné, cliquez sur **non**.

   L'action est annulée. *DataContext.Connection* conserve la connexion existante.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
