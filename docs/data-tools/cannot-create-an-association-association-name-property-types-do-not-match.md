---
title: Les types de propriété ne correspondent pas
description: Impossible de créer un Association-les types de propriété ne correspondent pas. Affichez des informations sur ce message de Concepteur Objet Relationnel Visual Studio (Concepteur O/R).
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bce5a285f3bccdc2be8004f0eba4546bb7964a42
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382050"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossible de créer une association &lt;nom de l’association&gt;. Les types de propriétés ne correspondent pas

Impossible de créer un Association \<association name> -les types de propriété ne correspondent pas. Les propriétés n’ont pas de types correspondants : \<property names> .

Les associations sont définies par les **Propriétés d’association** sélectionnées dans la boîte de dialogue **Éditeur d’associations**. Les propriétés de part et d'autre de l'association doivent avoir le même type de données.

Les propriétés répertoriées dans le message n'ont pas le même type de données.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message et prenez note des propriétés mentionnées dans le message.

2. Cliquez sur **OK** pour fermer la boîte de dialogue.

3. Inspectez les **Propriétés d’association** et sélectionnez des propriétés du même type de données.

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Comment : créer une association entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)