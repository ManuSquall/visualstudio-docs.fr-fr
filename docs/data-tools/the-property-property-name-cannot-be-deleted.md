---
title: La propriété ne peut pas être supprimée.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 80b5e40900cd8912b727270a46ebcf119c324f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La propriété \<nom de la propriété > ne peut pas être supprimé.

La propriété \<nom de la propriété > ne peut pas être supprimé, car il est défini comme le **propriété de discriminateur** pour l’héritage entre \<nom de la classe > et \<nom de la classe >

La propriété sélectionnée est définie comme la **propriété de discriminateur** pour l’héritage entre les classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.

Définir le **propriété de discriminateur** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le Concepteur O/R, sélectionnez la ligne d'héritage qui connecte les classes de données indiquées dans le message d'erreur.

2. Définir le **discriminateur** propriété à une autre propriété.

3. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)