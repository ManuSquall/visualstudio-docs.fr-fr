---
title: 'Comment : activer et désactiver (Concepteur O-R) la pluralisation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089381"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Comment : activer et désactiver (Concepteur O/R) la pluralisation
Par défaut, lorsque vous faites glisser des objets de base de données qui ont des noms se terminant par s ou ies de **Explorateur de serveurs** ou **Database Explorer** sur le [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), la noms des classes d’entité générées sont remplacés par au pluriel au singulier. C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données. Par exemple, l’ajout un `Customers` de la table vers le **Concepteur O/R** des résultats dans une classe d’entité nommée `Customer` , car la classe conserve les données pour un seul client.

> [!NOTE]
>  Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Pour activer et désactiver la pluralisation

1.  Dans le menu **Outils** , cliquez sur **Options**.

2.  Dans le **Options** boîte de dialogue, développez **outils de base de données**.

    > [!NOTE]
    >  Sélectionnez **afficher tous les paramètres** si le **outils de base de données** nœud n’est pas visible.

3.  Cliquez sur **Concepteur O/R**.

4.  Définissez **Pluralisation des noms** à **activé** = **False** pour définir le **Concepteur O/R** afin qu’il ne modifie pas les noms de classe .

5.  Définissez **Pluralisation des noms** à **activé** = **True** pour appliquer les règles de pluralisation aux noms de classes d’objets ajoutés à la **O/R Concepteur**.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)