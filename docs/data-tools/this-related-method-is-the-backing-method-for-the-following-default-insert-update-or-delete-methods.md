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
ms.openlocfilehash: a5ae70462079589ba2b63ee50cf0b7a0570e056a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457849"
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

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)