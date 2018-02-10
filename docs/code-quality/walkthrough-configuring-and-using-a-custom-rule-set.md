---
title: "Procédure pas à pas : Configuration et à l’aide d’un ensemble de règles | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b72a86f10c6e864406929fdccfb59bdd9393752e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé

Cette procédure pas à pas montre comment utiliser les outils d’analyse de code qui ont été configurés pour utiliser un texte personnalisé *ensemble de règles* sur une bibliothèque de classes. Vous pouvez sélectionner un ensemble de règles relatives au type de projet que vous avez spécifié pour votre solution, ou vous pouvez sélectionner les autres ensembles de règles pour répondre à un besoin spécifique, comme l’analyse du code hérité pour les problèmes qui peuvent être résolus de façon permanente. Dans les deux cas, les ensembles de règles peuvent également être personnalisées pour les adapter précisément aux besoins de votre projet.  
  
Dans cette procédure pas à pas, vous allez effectuer ces processus :  
  
-   Créer une bibliothèque de classes.  
  
-   Sélectionnez le **règles de conception de base Microsoft** ensemble de règles d’analyse du Code.  
  
-   Ajoutez votre propre code à la classe.  
  
-   Exécuter l’analyse du Code.  
  
-   Personnaliser l’ensemble de règles.  
  
-   Exécuter l’analyse du Code et voir la configuration de la règle fonctionne de comportement de personnalisation.  
  
## <a name="using-rule-sets-with-code-analysis"></a>À l’aide de la règle définit avec l’analyse du Code

Commencez par créer une bibliothèque de classes simple.  
  
### <a name="create-a-class-library"></a>Créer une bibliothèque de classes  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **Types de projets**, cliquez sur **Visual C#**.  
  
3.  Sous **Visual C#**, sélectionnez **bibliothèque de classes**.  
  
4.  Dans le **nom** zone de texte, tapez **RuleSetSample** puis cliquez sur **OK**.  
  
 Ensuite, vous allez sélectionner la **règles de conception de base Microsoft** ensemble de règles et l’enregistrer avec votre projet.  
  
### <a name="select-a-code-analysis-rule-set"></a>Sélectionnez un ensemble de règles code analysis  
  
1.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour RuleSetSample**.  
  
     Les paramètres de configuration pour l’analyse du Code s’affichent.  
  
2.  Dans le **exécuter cet ensemble de règles** la liste déroulante, sélectionnez **toutes les règles Microsoft**.  
  
     Pour plus d’informations sur les ensembles de règles disponibles, consultez [règle d’analyse du Code définie référence](../code-quality/code-analysis-rule-set-reference.md).  
  
     Dans le menu fichier, cliquez sur **enregistrer les éléments sélectionnés** pour mettre à jour le fichier projet avec plus d’informations sur l’ensemble de règles que vous avez sélectionné et ses paramètres.  
  
    > [!TIP]
    >  Dans une situation réelle, il est conseillé de pour hiérarchiser les problèmes que vous souhaitez cibler avec l’analyse du code pour commencer le **règles minimales recommandées** ensemble de règles et corriger les problèmes de votre choisis, puis ajouter de façon incrémentielle des règles ou une règle définit pour rechercher et corriger les problèmes supplémentaires.  
  
 Ensuite, vous allez ajouter du code à la bibliothèque de classes qui sera utilisée pour illustrer les violations de la CA1704 « Identificateurs doivent être correctement orthographiés » règle d’analyse du Code. Pour plus d’informations, consultez [CA1704 : les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Ajoutez votre propre code  
  
-   Dans l’Explorateur de solutions, ouvrez le fichier Class1.cs et remplacez le code existant avec les éléments suivants :  
  
    ```csharp
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }
    ```
  
Vous pouvez maintenant exécuter l’analyse du Code sur le projet RuleSetSample et recherchez les erreurs et les avertissements générés dans la fenêtre liste d’erreurs.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Exécuter l’analyse du Code sur le projet RuleSetSample  
  
1.  Sur le **analyser** menu, cliquez sur **exécuter l’analyse du Code sur RuleSetSample**.  
  
2.  Dans la fenêtre liste d’erreurs, cliquez sur **avertissements** puis cliquez sur le **Description** en-tête de colonne pour trier les avertissements dans l’ordre alphanumérique.  
  
     Dans une application réelle, vous serez corriger toute violation de règle à ce stade, ou si vous le souhaitez désactiver ou supprimer une règle si vous avez déterminé qu’il n’a pas impératif de les corriger. Pour plus d’informations, consultez [supprimer les avertissements](../code-quality/in-source-suppression-overview.md).
  
3.  Notez que les avertissements CA1704. Les violations de cette règle indiquent que « pensez en fournissant un nom plus significatif pour les paramètres. » Vous pouvez corriger le problème dans votre code, ou vous pouvez désactiver la règle, comme expliqué dans la procédure suivante.  
  
 Ensuite, vous allez personnaliser l’ensemble de règles pour exclure l’avertissement CA1704, « Identificateurs doit être correcte ».  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personnaliser l’ensemble de règles pour votre projet désactiver une règle spécifique  
  
1.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour RuleSetSample**.  
  
2.  Dans le **exécuter cet ensemble de règles** déroulante liste, vérifiez que le **toutes les règles Microsoft** est encore sélectionné de la règle, puis cliquez sur **ouvrir**. La page de jeu de règles s’affiche.  
  
3.  Développez le nœud de catégorie Microsoft.Naming, puis sélectionnez l’avertissement CA1704.  
  
4.  Sous le **Action** colonne, sélectionnez **None.** Cela empêche CA1704 de s’afficher comme un avertissement ou une erreur dans la fenêtre liste d’erreurs.  
  
     Maintenant est judicieux de faire des essais avec différents boutons de barre d’outils et pour vous familiariser avec les options de filtrage. Par exemple, vous pouvez utiliser la **Group By** liste déroulante, pour faciliter la recherche d’une règle spécifique, ou la catégorie de règles. Un autre exemple est que vous pouvez utiliser la **masquer les règles désactivées** bouton dans la barre d’outils des pages de jeu de règle pour masquer ou afficher toutes les règles avec la **Action** colonne définie sur **aucun**. Cela peut être utile si vous souhaitez effectuer une analyse des règles que vous avez désactivé pour vérifier que vous souhaitez toujours les désactivé.  
  
5.  Dans le menu Affichage, cliquez sur Propriétés. Type **ensemble de règles personnalisé Mes** dans la zone Nom de la fenêtre d’outil Propriétés. Cela modifie le nom complet de la nouvelle règle définie dans le [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer toutes les règles Microsoft.ruleset** enregistrer la règle personnalisée définie. Accédez au dossier racine de votre projet. Dans **le nom de fichier** zone de texte, tapez **MyCustomRuleSet**. L’ensemble de règles personnalisé peut maintenant être sélectionné pour une utilisation avec votre projet.  
  
Désormais avec votre nouvel ensemble de règles créé, vous devez configurer les paramètres du projet pour spécifier que vous souhaitez utiliser votre nouvel ensemble de règles avec.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Spécifiez la nouvelle règle pour une utilisation avec votre projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**.  
  
2.  Dans le **propriétés** , cliquez sur **l’analyse du Code**.  
  
     Dans le **exécuter cet ensemble de règles** la liste déroulante, cliquez sur  **\<Parcourir... >**. Accédez au dossier racine de votre projet de code, puis sélectionnez **MyCustomRuleSet.ruleset**. Il s’agit du nouvel ensemble de règles que vous avez créé dans la procédure précédente.  
  
3.  Sur le **fichier** menu, cliquez sur **enregistrer** pour enregistrer la configuration de votre projet. L’ensemble de règles personnalisé peut maintenant être utilisé avec votre projet.  
  
 Enfin, vous allez exécuter l’analyse du Code en utilisant votre ensemble de règles MyCustomRuleSet. Notez que la fenêtre liste d’erreurs n’affiche pas la violation de règle de performance CA1704.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Exécuter l’analyse du Code sur le projet RuleSetSample pour la deuxième fois  
  
1.  Sur le **analyser** menu, cliquez sur **exécuter l’analyse du Code sur RuleSetSample**.  
  
2.  Dans la fenêtre liste d’erreurs, notez que lorsque vous cliquez sur **avertissements**, vous ne voyez plus l’avertissement CA1704 concernant la règle « Identificateurs doit être correcte ».  
  
## <a name="see-also"></a>Voir aussi

[Comment : configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)