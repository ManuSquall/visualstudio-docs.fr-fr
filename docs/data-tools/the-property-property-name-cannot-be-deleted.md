---
title: Impossible de supprimer la propriété
description: La propriété ne peut pas être supprimée. Affichez des informations sur ce message de Concepteur Objet Relationnel Visual Studio (Concepteur O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bdca9758116c551604b5f75f141c15107c1fc890
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998358"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Impossible de supprimer la propriété \<property name>

La propriété \<property name> ne peut pas être supprimée, car elle est définie en tant que **propriété de discriminateur** pour l’héritage entre \<class name> et \<class name>

La propriété sélectionnée est définie comme **Propriété de discriminateur** pour l’héritage entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.

Affectez à **Propriété de discriminateur** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le **Concepteur O/R**, sélectionnez la ligne d’héritage qui connecte les classes de données indiquées dans le message d’erreur.

2. Affectez à **Propriété de discriminateur** une propriété différente.

3. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)