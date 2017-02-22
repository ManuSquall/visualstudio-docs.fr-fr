---
title: "Proc&#233;dure pas &#224; pas&#160;: configuration et utilisation d’un ensemble de r&#232;gles personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, procédures pas à pas"
  - "analyse du code, ensembles de règles"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# Proc&#233;dure pas &#224; pas&#160;: configuration et utilisation d’un ensemble de r&#232;gles personnalis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas indique comment utiliser les outils d'analyse du code configurés afin d'utiliser un *ensemble de règles* personnalisé sur une bibliothèque de classes.  Vous pouvez sélectionner un ensemble de règles relatif au type de projet que vous avez spécifié pour votre solution ou sélectionner d'autres ensembles de règles pour effectuer une tâche particulière, par exemple, analyser du code hérité pour les problèmes qui peuvent être résolus de façon permanente.  Dans l'un ou l'autre des cas, vous pouvez également personnaliser les ensembles de règles pour les adapter précisément aux exigences de votre projet.  
  
 Dans cette procédure pas à pas, vous allez effectuer les tâches suivantes :  
  
-   Créer une bibliothèque de classes.  
  
-   Sélectionner l'ensemble de règles d'analyse du code **Règles de conception de base Microsoft**.  
  
-   Ajouter votre propre code à la classe.  
  
-   Lancer l'analyse du code.  
  
-   Personnaliser l'ensemble de règles.  
  
-   Lancer l'analyse du code et voir comment se comporte la personnalisation de l'ensemble de règles.  
  
## Composants requis  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Utilisation des ensembles de règles avec l'analyse du code  
 En premier lieu, créez une bibliothèque de classes simple.  
  
#### Créer une bibliothèque de classes  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Types de projets**, cliquez sur **Visual C\#**.  
  
3.  Sous **Visual C\#**, sélectionnez **Bibliothèque de classes**.  
  
4.  Dans la zone de texte **Nom**, tapez RuleSetSample, puis cliquez sur **OK**.  
  
 Ensuite, sélectionnez l'ensemble de règles **Règles de conception de base Microsoft** et enregistrez\-le avec votre projet.  
  
#### Sélectionner un ensemble de règles d'analyse du code  
  
1.  Dans le menu **Analyser**, cliquez sur **Configurer l'analyse du code pour RuleSetSample**.  
  
     Les paramètres de configuration s'affichent pour l'analyse du code.  
  
2.  Dans la liste déroulante **Exécuter cet ensemble de règles**, sélectionnez **Toutes les règles Microsoft**.  
  
     Pour plus d'informations sur les ensembles de règles disponibles, consultez [Référence d’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md).  
  
     Dans le menu Fichier, cliquez sur **Enregistrer les éléments sélectionnés** pour mettre à jour le fichier projet avec les informations concernant l'ensemble de règles que vous avez sélectionné et ses paramètres.  
  
    > [!TIP]
    >  Dans une situation réelle, pour hiérarchiser les problèmes que vous souhaitez cibler avec l'analyse du code, il convient de commencer par l'ensemble de règles **Règles Microsoft minimales recommandées** et de corriger les problèmes prioritaires, puis d'ajouter des règles ou ensembles de règles par incrément, afin de rechercher et de corriger les problèmes restants.  
  
 Ensuite, il vous faut ajouter des éléments de code à la bibliothèque de classes qui sera utilisée pour mettre en évidence les violations à la règle d'analyse du code CA1704 « L'orthographe des identificateurs doit être correcte ».  Pour plus d'informations, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### Ajouter votre propre code  
  
-   Dans l'Explorateur de solutions, ouvrez le fichier Class1.cs et remplacez le code existant par les éléments suivants :  
  
    ```  
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
  
 Vous pouvez à présent lancer l'analyse du code sur le projet RuleSetSample et identifier les erreurs et avertissements générés dans la fenêtre Liste d'erreurs.  
  
#### Lancer l'analyse du code sur le projet RuleSetSample  
  
1.  Dans le menu **Analyser**, cliquez sur **Exécuter l'analyse du code sur RuleSetSample**.  
  
2.  Dans la fenêtre Liste d'erreurs, cliquez sur **Avertissements** puis sur l'en\-tête de colonne **Description** pour trier les avertissements dans l'ordre alphanumérique.  
  
     Dans une situation réelle, c'est à ce stade que vous résoudriez les problèmes de violation de règle ou éventuellement désactiveriez ou supprimeriez une règle s'il s'avérait qu'il était inutile de la corriger.  Pour plus d'informations, consultez [Supprimer des avertissements à l'aide de l'attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Lisez les avertissements CA1704.  Les violations de cette règle indiquent que vous devez donner un nom plus significatif pour les paramètres. Vous pourriez soit corriger le problème directement dans le code soit désactiver la règle, comme indiqué dans la procédure suivante.  
  
 Ensuite, vous personnalisez l'ensemble de règles pour exclure l'avertissement CA1704 « L'orthographe des identificateurs doit être correcte ».  
  
#### Personnaliser l'ensemble de règles associé à votre projet afin de désactiver une règle spécifique  
  
1.  Dans le menu **Analyser**, cliquez sur **Configurer l'analyse du code pour RuleSetSample**.  
  
2.  Dans la liste déroulante **Exécuter cet ensemble de règles**, vérifiez que l'ensemble de règles **Toutes les règles Microsoft** est encore sélectionné, puis cliquez sur **Ouvrir**.  La page de l'ensemble de règles s'affiche.  
  
3.  Développez le nœud de catégorie Microsoft.Naming, puis sélectionnez l'avertissement CA1704.  
  
4.  Sous la colonne **Action**, sélectionnez **Aucune**. Cela empêche CA1704 de s'afficher sous la forme d'un avertissement ou d'une erreur dans la fenêtre Liste d'erreurs.  
  
     Il convient à présent d'essayer les différents boutons et options de filtrage de la barre d'outils pour voir comment ils se comportent.  Par exemple, utilisez la liste déroulante **Grouper par** pour faciliter la recherche d'une règle ou d'une catégorie de règles spécifique.  Un autre exemple consisterait à utiliser le bouton **Masquer les règles désactivées** dans la barre d'outils des pages de l'ensemble de règles pour masquer ou afficher toutes les règles avec la colonne **Action** définie sur **Aucune**.  Cela peut être utile si vous souhaitez rechercher des règles que vous avez désactivées et confirmer qu'elles doivent le rester.  
  
5.  Dans le menu Affichage, cliquez sur Fenêtre Propriétés.  Tapez **My Custom Rule Set** dans la zone Nom de la fenêtre d'outil Propriétés.  Cela modifie le nom complet du nouvel ensemble de règles dans l'IDE de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  Dans le menu **Fichier**, cliquez sur **Enregistrer Toutes les règles Microsoft.ruleset** pour enregistrer votre ensemble de règles personnalisé.  Naviguez jusqu'au dossier racine de votre projet.  Dans la zone de texte **Nom de fichier**, tapez MyCustomRuleSet.  Vous pouvez désormais sélectionner l'ensemble de règles personnalisé pour l'utiliser avec votre projet.  
  
 Maintenant que vous avez créé un ensemble de règles, vous devez configurer les paramètres de votre projet de sorte à indiquer que vous souhaitez utiliser votre nouvel ensemble de règles avec.  
  
#### Définir le nouvel ensemble de règles à utiliser avec votre projet  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.  
  
2.  Dans l'onglet **Propriétés**, cliquez sur **Analyse du code**.  
  
     Dans la liste déroulante **Exécuter cet ensemble de règles**, cliquez sur **\<Parcourir..\>**.  Naviguez jusqu'au dossier racine de votre projet de code, puis sélectionnez MyCustomRuleSet.ruleset.  Il s'agit du nouvel ensemble de règles que vous avez créé à l'étape précédente.  
  
3.  Dans le menu **Fichier**, cliquez sur **Enregistrer** pour enregistrer la configuration de votre projet.  Vous pouvez à présent utiliser l'ensemble de règles personnalisé avec votre projet.  
  
 Pour finir, vous aller exécuter une nouvelle fois l'analyse du code avec votre ensemble de règles MyCustomRuleSet.  Remarquez que la fenêtre Liste d'erreurs n'affiche pas la violation de la règle de performance CA1704.  
  
#### Exécuter l'analyse du code sur le projet RuleSetSample une deuxième fois  
  
1.  Dans le menu **Analyser**, cliquez sur **Exécuter l'analyse du code sur RuleSetSample**.  
  
2.  Dans la fenêtre Liste d'erreurs, remarquez que si vous cliquez sur **Avertissements**, vous ne voyez plus l'avertissement CA1704 concernant la violation de la règle « L'orthographe des identificateurs doit être correcte ».  
  
## Voir aussi  
 [Procédure : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Référence d’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)