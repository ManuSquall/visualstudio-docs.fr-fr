---
title: Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc83bc78aace73cedf186b5ec925dce0a509b91d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945649"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut

Cette méthode associée est la méthode de stockage pour la valeur par défaut suivant `Insert`, `Update`, ou `Delete` méthodes. Si vous la supprimez, ces méthodes seront aussi supprimées. Voulez-vous continuer ?

Le texte sélectionné `DataContext` méthode est actuellement utilisée comme l’un de la `Insert`, `Update`, ou `Delete` méthodes pour l’une des classes d’entité sur le **Concepteur O/R**. Supprimer les causes de la méthode sélectionnée la classe d’entité qui a été à l’aide de cette méthode pour rétablir le comportement d’exécution par défaut pour l’exécution de l’instruction insert, update ou delete pendant une mise à jour.

## <a name="selected-method-options"></a>Options de la méthode sélectionnée

- Pour supprimer la méthode sélectionnée, à l’origine de la classe d’entité à utiliser les mises à jour de l’exécution, cliquez sur **Oui**.

   La méthode sélectionnée est supprimée et toutes les classes qui ont utilisé cette méthode pour substituer le comportement de mise à jour sont réinitialisées à la valeur par défaut du comportement au moment de l'exécution par défaut LINQ to SQL.

- Pour fermer la boîte de message, en laissant la méthode sélectionnée inchangée, cliquez sur **non**.

   La boîte de message se ferme et aucune modification n'est apportée.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)