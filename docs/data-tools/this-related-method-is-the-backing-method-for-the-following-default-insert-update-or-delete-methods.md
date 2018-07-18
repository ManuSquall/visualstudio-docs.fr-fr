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
ms.openlocfilehash: fdb359ebe4a42e0ddad8b93c1e746922ac609f60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922481"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut

Cette méthode associée est la méthode de stockage pour les méthodes par défaut d'insertion, de mise à jour ou de suppression suivantes. Si vous la supprimez, ces méthodes seront aussi supprimées. Voulez-vous continuer ?

La méthode `DataContext` sélectionnée est actuellement utilisée comme l'une des méthodes d'insertion, de mise à jour et de suppression pour l'une des classes d'entité dans le Concepteur O/R. La suppression de la méthode sélectionnée provoquera, pour la classe d'entité qui l'utilisait, le retour au comportement au moment de l'exécution par défaut pour les méthodes d'insertion, de mise à jour et de suppression lors d'une mise à jour.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Pour supprimer la méthode sélectionnée et obliger la classe d'entité à utiliser des mises à jour au moment de l'exécution

- Cliquez sur **Oui**.

    La méthode sélectionnée est supprimée et toutes les classes qui ont utilisé cette méthode pour substituer le comportement de mise à jour sont réinitialisées à la valeur par défaut du comportement au moment de l'exécution par défaut LINQ to SQL.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Pour fermer le message en laissant la méthode sélectionnée inchangée

- Cliquez sur **Non**.

    La boîte de message se ferme et aucune modification n'est apportée.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)