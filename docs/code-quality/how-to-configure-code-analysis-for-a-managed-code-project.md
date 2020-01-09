---
title: Configurer l’analyse du Code
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
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587561"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Comment : configurer l’analyse héritée pour le code managé

Dans Visual Studio, vous pouvez choisir dans une liste d’ensembles de [règles](../code-quality/rule-set-reference.md) d’analyse du code à appliquer à un projet de code managé. Par défaut, le **règles minimales recommandées par Microsoft** ensemble de règles est sélectionné, mais vous pouvez appliquer une autre règle définie si vous le souhaitez. Ensembles de règles peuvent être appliquées à un ou plusieurs projets dans une solution.

> [!NOTE]
> Cet article s’applique à l’analyse héritée et non aux [analyseurs de code basés sur .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurer un ensemble de règles pour un projet .NET Framework

1. Ouvrez le **analyse du Code** onglet sur les pages de propriétés du projet. Plusieurs méthodes sont possibles :

   - Dans **l’Explorateur de solutions**, sélectionnez le projet. Dans la barre de menus, sélectionnez **analyser** > **configurer l’analyse du Code** > **pour \<nom_projet >** .

   - Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **propriétés**, puis sélectionnez le **analyse du Code** onglet.

2. Dans le **Configuration** et **plateforme** listes, sélectionnez la plateforme de configuration et la cible de génération.

::: moniker range="vs-2017"

3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez **activer l’analyse du code sur la build**. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur \<nom_projet >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez **exécuter lors de la génération** dans la section **analyseurs binaires** . Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur \<nom_projet >** .

::: moniker-end

4. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source d’un formulaire ou d’un modèle, et il ne sera pas remplacé.

::: moniker range="vs-2017"

5. Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :

::: moniker-end

::: moniker range=">=vs-2019"

5. Dans la liste **règles actives** , effectuez l’une des opérations suivantes :

::: moniker-end

   - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

   - Sélectionnez **\<parcourir >** pour rechercher un ensemble de règles personnalisées existant qui ne figure pas dans la liste.

   - Définir un [ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Spécifier des ensembles de règles pour plusieurs projets dans une solution

Par défaut, tous les projets gérés d’une solution sont affectés les *règles minimales recommandées par Microsoft* ensemble de règles d’analyse du code. Vous pouvez modifier les ensembles de règles qui sont assignés aux projets d’une solution dans le **propriétés** boîte de dialogue pour la solution.

1. Ouvrez la solution dans Visual Studio.

2. Sur le **analyser** menu, sélectionnez **configurer l’analyse du Code pour la Solution**.

3. Si nécessaire, développez **propriétés communes**, puis sélectionnez **paramètres d’analyse de Code**.

4. Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets :

    - Pour spécifier un ensemble de règles pour un projet individuel, sélectionnez le nom du projet.

    - Pour spécifier un ensemble de règles pour plusieurs projets, maintenez la touche **Ctrl** et sélectionnez les noms de projet.

    - Pour spécifier tous les projets dans la solution, maintenez la touche **MAJ** et cliquez sur dans la liste des projets.

5. Sélectionnez le **l’ensemble de règles** champ d’un projet, puis sélectionnez le nom de la règle défini que vous souhaitez appliquer.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
