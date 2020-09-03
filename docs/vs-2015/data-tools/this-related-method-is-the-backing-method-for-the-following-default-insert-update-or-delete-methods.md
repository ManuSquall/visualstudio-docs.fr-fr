---
title: Cette méthode associée est la méthode de stockage pour les méthodes d’insertion, de mise à jour ou de suppression par défaut suivantes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667179"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Cette méthode associée est la méthode de sauvegarde des méthodes d'insertion, de mise à jour ou de suppression par défaut
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette méthode associée est la méthode de stockage pour les méthodes par défaut d'insertion, de mise à jour ou de suppression suivantes. Si vous la supprimez, ces méthodes seront aussi supprimées. Voulez-vous continuer ?

 La méthode `DataContext` sélectionnée est actuellement utilisée comme l'une des méthodes d'insertion, de mise à jour et de suppression pour l'une des classes d'entité dans le Concepteur O/R. La suppression de la méthode sélectionnée provoquera, pour la classe d'entité qui l'utilisait, le retour au comportement au moment de l'exécution par défaut pour les méthodes d'insertion, de mise à jour et de suppression lors d'une mise à jour.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Pour supprimer la méthode sélectionnée et obliger la classe d'entité à utiliser des mises à jour au moment de l'exécution

- Cliquez sur **Oui**.

     La méthode sélectionnée est supprimée et toutes les classes qui ont utilisé cette méthode pour substituer le comportement de mise à jour sont réinitialisées à la valeur par défaut du comportement au moment de l'exécution par défaut LINQ to SQL.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Pour fermer le message en laissant la méthode sélectionnée inchangée

- Cliquez sur **Non**.

     La boîte de message se ferme et aucune modification n'est apportée.

## <a name="see-also"></a>Voir aussi
 [Méthode DataContext (concepteur o/r)](../data-tools/datacontext-methods-o-r-designer.md) [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (concepteur o/r)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
