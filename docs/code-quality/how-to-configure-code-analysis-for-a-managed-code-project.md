---
title: Configurer l’analyse du code
ms.date: 04/04/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c94742b452bfd665dc35c59ef831bca2cdacf1f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801046"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Comment : configurer l’analyse héritée pour le code managé

Dans Visual Studio, vous pouvez choisir dans une liste d’ensembles de [règles](../code-quality/rule-set-reference.md) d’analyse du code à appliquer à un projet de code managé. Par défaut, l’ensemble de règles **règles minimales recommandées Microsoft** est sélectionné, mais vous pouvez appliquer un autre ensemble de règles si vous le souhaitez. Les ensembles de règles peuvent être appliqués à un ou plusieurs projets d’une solution.

> [!NOTE]
> Cet article s’applique à l’analyse héritée et non aux [analyseurs de code basés sur .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurer un ensemble de règles pour un projet .NET Framework

1. Ouvrez l’onglet **analyse du code** dans les pages de propriétés du projet. Plusieurs méthodes sont possibles :

   - Dans **Explorateur de solutions**, choisissez le projet. Dans la barre de menus, sélectionnez **analyser**  >  **configurer l’analyse**  >  **du code pour \<projectname> **.

   - Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, sélectionnez **Propriétés**, puis sélectionnez l’onglet **analyse du code** .

2. Dans les listes **configuration** et **plateforme** , choisissez la configuration de build et la plateforme cible.

::: moniker range="vs-2017"

3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez **activer l’analyse du code sur la build**. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **analyser**  >  **exécuter**l’analyse  >  **du \<projectname> code exécuter l’analyse du code sur **.

::: moniker-end

::: moniker range=">=vs-2019"

3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez **exécuter lors de la génération** dans la section **analyseurs binaires** . Vous pouvez également exécuter manuellement l’analyse du code hérité. pour plus d’informations, consultez [Comment : exécuter manuellement l’analyse du code hérité pour le code managé](how-to-run-legacy-code-analysis-manually-for-managed-code.md) .

::: moniker-end

4. Pour afficher les avertissements du code généré, désactivez la case à cocher **Supprimer les résultats du code généré** .

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source d’un formulaire ou d’un modèle, et il ne sera pas remplacé.

::: moniker range="vs-2017"

5. Dans la liste **exécuter cet ensemble de règles** , effectuez l’une des opérations suivantes :

::: moniker-end

::: moniker range=">=vs-2019"

5. Dans la liste **règles actives** , effectuez l’une des opérations suivantes :

::: moniker-end

   - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

   - Sélectionnez **\<Browse>** cette option pour rechercher un ensemble de règles personnalisées existant qui ne figure pas dans la liste.

   - Définissez un [ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Spécifier des ensembles de règles pour plusieurs projets dans une solution

Par défaut, tous les projets managés d’une solution se voient affecter l’ensemble de règles d’analyse du code des *règles minimales recommandées Microsoft* . Vous pouvez modifier les ensembles de règles qui sont affectés aux projets d’une solution dans la boîte de dialogue **Propriétés** de la solution.

1. Ouvrez la solution dans Visual Studio.

2. Dans le menu **analyser** , sélectionnez **configurer l’analyse du code pour la solution**.

3. Si nécessaire, développez **Propriétés communes**, puis sélectionnez **paramètres d’analyse du code**.

4. Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets :

    - Pour spécifier un ensemble de règles pour un projet individuel, choisissez le nom du projet.

    - Pour spécifier un ensemble de règles pour plusieurs projets, sélectionnez **CTRL** et les noms de projet.

    - Pour spécifier tous les projets de la solution, sélectionnez **Shift** et la liste de projets.

5. Sélectionnez le champ **ensemble de règles** d’un projet, puis sélectionnez le nom de l’ensemble de règles que vous souhaitez appliquer.

## <a name="see-also"></a>Voir aussi

- [Référence d’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)
