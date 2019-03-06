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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 466178015c725242b6bc4a28da1da6ded19b421f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916789"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procédure : Configurer l’analyse du code pour un projet de code managé

Dans Visual Studio, vous pouvez choisir parmi une liste de l’analyse du code [ensembles de règles](../code-quality/rule-set-reference.md)) à appliquer à un projet de code managé. Par défaut, le **règles minimales recommandées par Microsoft** ensemble de règles est sélectionné, mais vous pouvez appliquer une autre règle définie si vous le souhaitez. Ensembles de règles peuvent être appliquées à un ou plusieurs projets dans une solution.

> [!TIP]
> Pour plus d’informations sur la configuration d’un ensemble de règles pour les applications web ASP.NET, consultez [Comment : Configurer l’analyse du Code pour un site web ASP.NET Application](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Pour configurer un ensemble de règles pour un projet .NET Framework

1. Ouvrez le **analyse du Code** onglet sur les pages de propriétés du projet. Vous pouvez le faire dans une des manières suivantes :

   - Dans **l’Explorateur de solutions**, sélectionnez le projet. Dans la barre de menus, sélectionnez **analyser** > **configurer l’analyse du Code** > **pour \<nom_projet >**.

   - Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **propriétés**, puis sélectionnez le **analyse du Code** onglet.

1. Dans le **Configuration** et **plateforme** listes, sélectionnez la plateforme de configuration et la cible de génération.

1. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez le **activer l’analyse du Code sur la Build** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur \<nom_projet >**.

1. Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.

    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et mettre à jour le code source pour un formulaire ou un modèle, sans que celle-ci n’est remplacé.

1. Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :

    - Sélectionnez l’ensemble de règles que vous souhaitez utiliser.

    - Sélectionnez  **\<Parcourir... >** pour trouver une règle personnalisée existante définie qui n’est pas dans la liste.

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
- [Guide pratique pour Configurer l’analyse du Code pour un site web ASP.NET Application](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)