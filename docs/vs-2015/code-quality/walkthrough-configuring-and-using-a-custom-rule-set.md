---
title: 'Procédure pas à pas : Configuration et utilisation d’un ensemble de règles personnalisé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645737"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Procédure pas à pas : Configuration et utilisation d’un ensemble de règles personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment utiliser les outils d’analyse du code qui ont été configurés pour utiliser un *ensemble de règles* personnalisé sur une bibliothèque de classes. Vous pouvez sélectionner un ensemble de règles qui se réfère au type de projet que vous avez spécifié pour votre solution, ou vous pouvez sélectionner d’autres ensembles de règles pour satisfaire à un besoin spécifique, par exemple l’analyse de code hérité pour les problèmes qui peuvent être résolus de manière sans rupture. Dans les deux cas, les ensembles de règles peuvent également être personnalisés pour affiner les exigences de votre projet.

 Dans cette procédure pas à pas, vous allez effectuer les étapes suivantes :

- Créer une bibliothèque de classes.

- Sélectionnez l’ensemble de règles d’analyse du code **règles de conception de base Microsoft** .

- Ajoutez votre propre code à la classe.

- Exécutez l’analyse du code.

- Personnaliser l’ensemble de règles.

- Exécutez l’analyse du code et observez le fonctionnement du comportement de personnalisation de l’ensemble de règles.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]ou [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Utilisation d’ensembles de règles avec l’analyse du code
 Tout d’abord, créez une bibliothèque de classes simple.

#### <a name="create-a-class-library"></a>Créer une bibliothèque de classes

1. Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**.

2. Dans la boîte de dialogue **nouveau projet** , sous **types de projets**, cliquez sur **visuel C#** .

3. Sous **visuel C#** , sélectionnez **bibliothèque de classes**.

4. Dans la zone de texte **nom** , tapez **RuleSetSample** , puis cliquez sur **OK**.

   Ensuite, vous allez sélectionner l’ensemble de règles des **règles de conception de base Microsoft** et l’enregistrer dans votre projet.

#### <a name="select-a-code-analysis-rule-set"></a>Sélectionner un ensemble de règles d’analyse du code

1. Dans le menu **analyser** , cliquez sur **configurer l’analyse du code pour RuleSetSample**.

    Les paramètres de configuration de l’analyse du code s’affichent.

2. Dans la liste déroulante **exécuter cet ensemble de règles** , sélectionnez **toutes les règles Microsoft**.

    Pour plus d’informations sur les ensembles de règles disponibles, consultez Référence de l' [ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md).

    Dans le menu fichier, cliquez sur **enregistrer les éléments sélectionnés** pour mettre à jour le fichier projet avec les informations relatives à l’ensemble de règles que vous avez sélectionné et à ses paramètres.

   > [!TIP]
   > Dans une situation réelle, une bonne pratique pour déterminer les problèmes que vous souhaitez cibler avec l’analyse du code consiste à démarrer avec l’ensemble de règles de **règles minimales recommandées** et à corriger les problèmes souhaités, puis à ajouter de façon incrémentielle d’autres règles ou ensembles de règles à Recherchez et corrigez les problèmes supplémentaires.

   Ensuite, vous allez ajouter du code à la bibliothèque de classes qui sera utilisée pour démontrer les violations de la règle d’analyse du code ca1704s « les identificateurs doivent être correctement orthographiés ». Pour plus d’informations, consultez [CA1704 : Les identificateurs doivent être orthographiés correctement ](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Ajouter votre propre code

- Dans Explorateur de solutions, ouvrez le fichier Class1.cs et remplacez le code existant par ce qui suit :

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

  Vous pouvez maintenant exécuter l’analyse du code sur le projet RuleSetSample et rechercher les erreurs et les avertissements générés dans la fenêtre Liste d’erreurs.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Exécuter l’analyse du code sur le projet RuleSetSample

1. Dans le menu **analyser** , cliquez sur **exécuter l’analyse du code sur RuleSetSample**.

2. Dans la fenêtre Liste d’erreurs, cliquez sur **avertissements** , puis cliquez sur l’en-tête de colonne **Description** pour trier les avertissements dans l’ordre alphanumérique.

    Dans une application réelle, vous devez corriger toutes les violations de règle qui méritent une correction à ce stade, ou vous pouvez désactiver ou supprimer une règle si vous avez déterminé qu’il n’était pas nécessaire de la corriger. Pour plus d’informations, consultez [Supprimer des avertissements à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Notez les avertissements CA1704. Ces violations sur cette règle indiquent que vous devez fournir un nom plus explicite pour les paramètres. Vous pouvez corriger le problème dans votre code ou désactiver la règle, comme expliqué dans la procédure suivante.

   Ensuite, vous allez personnaliser l’ensemble de règles pour exclure l’avertissement CA1704, « les identificateurs doivent être orthographiés correctement ».

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personnaliser l’ensemble de règles pour votre projet pour désactiver une règle spécifique

1. Dans le menu **analyser** , cliquez sur **configurer l’analyse du code pour RuleSetSample**.

2. Dans la liste déroulante **exécuter cet ensemble de règles** , vérifiez que l’ensemble de règles **Microsoft All Rules** est toujours sélectionné, puis cliquez sur **ouvrir**. La page ensemble de règles s’affiche.

3. Développez le nœud catégorie Microsoft. Naming, puis sélectionnez l’avertissement CA1704.

4. Sous la colonne **action** , sélectionnez **aucune.** Cela empêche CA1704 de s’afficher sous la forme d’un avertissement ou d’une erreur dans la fenêtre de Liste d’erreurs.

    Il est maintenant judicieux de faire des essais avec les différents boutons de la barre d’outils et les options de filtrage pour vous familiariser avec eux. Par exemple, vous pouvez utiliser la liste déroulante **regrouper par** pour faciliter la localisation d’une règle spécifique ou d’une catégorie de règles. Autre exemple : vous pouvez utiliser le bouton **Masquer les règles désactivées** dans la barre d’outils pages d’ensemble de règles pour masquer ou afficher toutes les règles dont la colonne **action** est définie sur **aucune**. Cela peut être utile si vous souhaitez rechercher les règles que vous avez désactivées pour vérifier que vous souhaitez toujours les désactiver.

5. Dans le menu Affichage, cliquez sur Fenêtre Propriétés. Tapez **mon ensemble de règles personnalisé** dans la zone nom de la fenêtre outil des propriétés. Cela modifie le nom complet du nouvel ensemble de règles dans l’IDE [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

6. Dans le menu **fichier** , cliquez sur **enregistrer Microsoft All Rules. RuleSet** pour enregistrer votre ensemble de règles personnalisé. Accédez au dossier racine de votre projet. Dans **la** zone de texte nom de fichier, tapez **MyCustomRuleSet**. L’ensemble de règles personnalisé peut maintenant être sélectionné pour être utilisé avec votre projet.

   Une fois votre nouvel ensemble de règles créé, vous devez configurer les paramètres de votre projet pour spécifier que vous souhaitez utiliser votre nouvel ensemble de règles.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Spécifier le nouvel ensemble de règles à utiliser avec votre projet

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Dans l’onglet **Propriétés** , cliquez sur **analyse du code**.

    Dans la liste déroulante **exécuter cet ensemble de règles** , cliquez sur **\<Browse.. >** . Accédez au dossier racine de votre projet de code, puis sélectionnez **MyCustomRuleSet. RuleSet**. Il s’agit du nouvel ensemble de règles que vous avez créé dans la procédure précédente.

3. Dans le menu **fichier** , cliquez sur **Enregistrer** pour enregistrer la configuration de votre projet. L’ensemble de règles personnalisé peut maintenant être utilisé avec votre projet.

   Enfin, vous allez réexécuter l’analyse du code à l’aide de votre ensemble de règles MyCustomRuleSet. Notez que la fenêtre de Liste d’erreurs n’affiche pas la violation de règle de performance CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Exécuter l’analyse du code sur le projet RuleSetSample pour la deuxième fois

1. Dans le menu **analyser** , cliquez sur **exécuter l’analyse du code sur RuleSetSample**.

2. Dans la fenêtre Liste d’erreurs, Notez que lorsque vous cliquez sur **avertissements**, vous ne voyez plus les violations d’avertissement ca1704s pour la règle « les identificateurs doivent être correctement orthographiés ».

## <a name="see-also"></a>Voir aussi
 [Guide pratique : Configurer l’analyse du code pour un projet de code managé ](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) référence de l' [ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)
