---
title: Guide pratique pour activer et désactiver la pluralisation (Concepteur O/R)
description: Savoir comment activer et désactiver la pluralisation dans Concepteur Objet Relationnel (Concepteur O/R). Le paramètre par défaut convertit les noms pluriels au singulier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 609af4ef71a6ed73bd1d9599d76d8eb64073efd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858694"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Guide pratique pour activer et désactiver la pluralisation (Concepteur O/R)
Par défaut, lorsque vous faites glisser des objets de base de données dont le nom se termine par un ou plusieurs **Explorateur de serveurs** ou **Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), les noms des classes d’entité générées sont modifiés du pluriel au singulier. C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données. Par exemple, l’ajout d’une `Customers` table au **Concepteur O/R** entraîne la création d’une classe d’entité nommée `Customer` parce que la classe contiendra des données pour un seul client.

> [!NOTE]
> Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Pour activer et désactiver la pluralisation

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Dans la boîte de dialogue **Options**, développez **Outils de base de données**.

    > [!NOTE]
    > Sélectionnez **Afficher tous les paramètres** si le nœud **Outils de base de données** n’est pas visible.

3. Cliquez sur **Concepteur O/R**.

4. Affectez à la **pluralisation des noms** la valeur **Enabled**  =  **false** pour définir le **Concepteur O/R** afin qu’il ne modifie pas les noms de classe.

5. Attribuez la **valeur** true à la **pluralisation des noms** pour  =   appliquer les règles de pluralité aux noms des classes des objets ajoutés au **Concepteur O/R**.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
