---
title: Guide pratique pour activer et désactiver la pluralisation (Concepteur O/R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 54b3376f9388116f179e2b09bcd136a37f3029f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586443"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Guide pratique pour activer et désactiver la pluralisation (Concepteur O/R)
Par défaut, lorsque vous faites glisser des objets de base de données dont le nom se termine par un ou plusieurs **Explorateur de serveurs** ou **Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), les noms des classes d’entité générées sont modifiés du pluriel au singulier. C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données. Par exemple, l’ajout d’une `Customers` table au **Concepteur O/R** génère une classe d’entité nommée `Customer`, car la classe contiendra des données pour un seul client.

> [!NOTE]
> Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Pour activer et désactiver la pluralisation

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Dans la boîte de dialogue **Options**, développez **Outils de base de données**.

    > [!NOTE]
    > Sélectionnez **Afficher tous les paramètres** si le nœud **Outils de base de données** n’est pas visible.

3. Cliquez sur **Concepteur O/R**.

4. Définissez la **pluralisation des noms** sur **activé** = **false** pour définir le **Concepteur O/R** afin qu’il ne modifie pas les noms de classe.

5. Définissez la **pluralisation des noms** sur **activé** = **true** pour appliquer des règles de pluralité aux noms de classes des objets ajoutés au **Concepteur O/R**.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
