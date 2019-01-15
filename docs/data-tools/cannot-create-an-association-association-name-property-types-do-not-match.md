---
title: Impossible de créer une association, les types de propriétés ne correspondent pas
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 1d0ed4ba38f93d57c8f8ab18245155dbd9013a5f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880635"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossible de créer une association &lt;nom de l’association&gt;. Les types de propriétés ne correspondent pas

Impossible de créer une association \<nom de l’association>. Les types de propriétés ne correspondent pas. Les propriétés n’ont pas de types correspondants : \<noms des propriétés>.

Les associations sont définies par les **Propriétés d’association** sélectionnées dans la boîte de dialogue **Éditeur d’associations**. Les propriétés de part et d'autre de l'association doivent avoir le même type de données.

Les propriétés répertoriées dans le message n'ont pas le même type de données.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message et prenez note des propriétés mentionnées dans le message.

2. Cliquez sur **OK** pour fermer la boîte de dialogue.

3. Inspectez les **Propriétés d’association** et sélectionnez des propriétés du même type de données.

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Guide pratique pour Créer une association entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)