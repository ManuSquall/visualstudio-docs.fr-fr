---
title: Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 252303c4933501dd3a4672329d66ef4910238a08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535250"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut

Cette méthode associée est la méthode de stockage pour les méthodes par défaut `Insert` , `Update` ou `Delete` . Si vous la supprimez, ces méthodes seront aussi supprimées. Voulez-vous continuer ?

La `DataContext` méthode sélectionnée est actuellement utilisée comme l’une des `Insert` `Update` méthodes, ou `Delete` pour l’une des classes d’entité sur le **Concepteur O/R**. La suppression de la méthode sélectionnée entraîne la classe d’entité qui utilisait cette méthode pour rétablir le comportement par défaut au moment de l’exécution pour effectuer l’insertion, la mise à jour ou la suppression pendant une mise à jour.

## <a name="selected-method-options"></a>Options de méthode sélectionnées

- Pour supprimer la méthode sélectionnée, ce qui entraîne l’utilisation des mises à jour du Runtime par la classe d’entité, cliquez sur **Oui**.

   La méthode sélectionnée est supprimée et toutes les classes qui utilisent cette méthode pour remplacer le comportement de mise à jour sont rétablies en utilisant le comportement par défaut LINQ to SQL au moment de l’exécution.

- Pour fermer la boîte de message, en laissant la méthode sélectionnée inchangée, cliquez sur **non**.

   La boîte de message se ferme et aucune modification n'est apportée.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)