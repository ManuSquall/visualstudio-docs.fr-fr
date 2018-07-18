---
title: Impossible de créer une association - propriété types ne correspondent pas
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7f0ef5829c89a10dcf985d0815ae8144b6cb791b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920176"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossible de créer une association &lt;nom de l’association&gt; -types de propriété ne correspondent pas

Impossible de créer une association \<nom de l’association >-types de propriété ne correspondent pas. Propriétés n’ont pas de types correspondants : \<les noms de propriétés >.

Les associations sont définies par le **propriétés d’Association** dans les **Éditeur d’associations** boîte de dialogue. Les propriétés de part et d'autre de l'association doivent avoir le même type de données.

Les propriétés répertoriées dans le message n'ont pas le même type de données.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message et prenez note des propriétés mentionnées dans le message.

2. Cliquez sur **OK** pour fermer la boîte de dialogue.

3. Inspecter le **propriétés d’Association** , puis sélectionnez Propriétés du même type de données.

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Comment : créer une association entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)