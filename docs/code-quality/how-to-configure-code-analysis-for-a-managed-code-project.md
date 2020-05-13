---
title: Configurer l’analyse du code
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431350"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Comment : Configurer l’analyse de l’héritage pour le code géré

Dans Visual Studio, vous pouvez choisir parmi une liste [d’ensembles](../code-quality/rule-set-reference.md) de règles d’analyse de code à appliquer à un projet de code géré. Par défaut, l’ensemble de règles **Microsoft Minimum Recommended Rules** est sélectionné, mais vous pouvez appliquer un ensemble de règles différent si désiré. Les ensembles de règles peuvent être appliqués à un ou plusieurs projets dans le monde d’une solution.

> [!NOTE]
> Cet article s’applique à l’analyse héritée et non aux [analyseurs de code basés sur la plate-forme de compilateur .NET](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurer une règle définie pour un projet cadre .NET

1. Ouvrez l’onglet **Analyse de code** sur les pages de propriété du projet. Plusieurs méthodes sont possibles :

   - Dans **Solution Explorer**, sélectionnez le projet. Sur la barre de menu, **sélectionnez Analyse** > de code > **configuré****pour \<le nom de projet>**.

   - Cliquez à droite sur le projet dans **Solution Explorer** et sélectionnez **les propriétés,** puis sélectionnez **l’onglet Analyse de code.**

2. Dans les listes **Configuration** et **Plate-forme,** sélectionnez la configuration de construction et la plate-forme cible.

::: moniker range="vs-2017"

3. Pour exécuter l’analyse de code chaque fois que le projet est construit à l’aide de la configuration sélectionnée, **sélectionnez Activez l’analyse du code sur Build**. Vous pouvez également exécuter l’analyse de code manuellement en sélectionnant Analyse > **de code d’analyse de code** > **d’analyse d’analyse \<d’analyse sur le nom de projet>**. **Analyze**

::: moniker-end

::: moniker range=">=vs-2019"

3. Pour exécuter l’analyse de code chaque fois que le projet est construit à l’aide de la configuration sélectionnée, **sélectionnez Exécuter sur la partie de build** dans la section Analyse **binaire.** Vous pouvez également exécuter l’analyse de code héritée manuellement, voir [Comment : Exécuter l’analyse de code hérité manuellement pour le code géré](how-to-run-legacy-code-analysis-manually-for-managed-code.md) pour plus de détails.

::: moniker-end

4. Pour afficher les avertissements à partir du code généré, effacez les résultats Supprimer à partir de la case à cocher **de code générée.**

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez à la fois afficher et maintenir le code source pour un formulaire ou un modèle, et il ne sera pas écrasé.

::: moniker range="vs-2017"

5. Dans la **course de cette liste de règles,** faites l’un des éléments suivants :

::: moniker-end

::: moniker range=">=vs-2019"

5. Dans la liste **des règles Actives,** faites l’une des suivantes :

::: moniker-end

   - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

   - Sélectionnez Parcourir ** \<>** pour trouver un ensemble de règles personnalisées existant qui n’est pas dans la liste.

   - Définir un [ensemble de règles personnalisées](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Spécifier les ensembles de règles pour plusieurs projets dans une solution

Par défaut, tous les projets gérés d’une solution se voient attribuer la règle d’analyse du code *Microsoft Minimum Recommended Rules.* Vous pouvez modifier les ensembles de règles qui sont affectés aux projets d’une solution dans la boîte de dialogue **Propriétés** pour la solution.

1. Ouvrez la solution dans Visual Studio.

2. Sur le menu **Analyze,** **sélectionnez Configurer l’analyse du code pour la solution**.

3. Si nécessaire, étendre **les propriétés communes,** puis sélectionner les **paramètres d’analyse de code**.

4. Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets :

    - Pour spécifier une règle définie pour un projet individuel, sélectionnez le nom du projet.

    - Pour spécifier une règle définie pour plusieurs projets, maintenez **Ctrl** et sélectionnez les noms du projet.

    - Pour spécifier tous les projets de la solution, maintenez **Shift** et cliquez sur la liste du projet.

5. Sélectionnez le champ **Rule Set** d’un projet, puis sélectionnez le nom de l’ensemble de règles que vous souhaitez appliquer.

## <a name="see-also"></a>Voir aussi

- [Référence d’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
