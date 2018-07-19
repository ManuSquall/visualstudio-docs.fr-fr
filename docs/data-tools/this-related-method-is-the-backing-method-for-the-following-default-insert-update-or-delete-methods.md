---
title: Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 30e08cb10b6e1912fe5962620faf34a1c6250cf3
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174155"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut

Cette méthode associée est la méthode de stockage pour la valeur par défaut suivant `Insert`, `Update`, ou `Delete` méthodes. Si vous la supprimez, ces méthodes seront aussi supprimées. Voulez-vous continuer ?

Le texte sélectionné `DataContext` méthode est actuellement utilisée comme l’un de la `Insert`, `Update`, ou `Delete` méthodes pour l’une des classes d’entité sur le **Concepteur O/R**. Supprimer les causes de la méthode sélectionnée la classe d’entité qui a été à l’aide de cette méthode pour rétablir le comportement d’exécution par défaut pour l’exécution de l’instruction insert, update ou delete pendant une mise à jour.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Pour supprimer la méthode sélectionnée et obliger la classe d'entité à utiliser des mises à jour au moment de l'exécution

- Cliquez sur **Oui**.

    La méthode sélectionnée est supprimée et toutes les classes qui ont utilisé cette méthode pour substituer le comportement de mise à jour sont réinitialisées à la valeur par défaut du comportement au moment de l'exécution par défaut LINQ to SQL.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Pour fermer le message en laissant la méthode sélectionnée inchangée

- Cliquez sur **Non**.

    La boîte de message se ferme et aucune modification n'est apportée.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)