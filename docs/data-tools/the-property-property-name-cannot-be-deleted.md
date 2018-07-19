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
ms.openlocfilehash: 7e85860de7494ae7d93ad37bd0a115fa786f0a87
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174011"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La propriété \<nom_propriété > ne peut pas être supprimé.

La propriété \<nom de propriété > ne peut pas être supprimé, car il est défini comme le **propriété de discriminateur** pour l’héritage entre \<nom de la classe > et \<nom de la classe >

La propriété sélectionnée est définie comme le **propriété de discriminateur** pour l’héritage entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.

Définir le **propriété de discriminateur** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le **Concepteur O/R**, sélectionnez la ligne d’héritage qui connecte les classes de données indiquée dans le message d’erreur.

2. Définir le **discriminateur** propriété une propriété différente.

3. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)