---
title: 'Démarrage rapide : analyse du code pour C-C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278482"
---
# <a name="quick-start-code-analysis-for-cc"></a>Démarrage rapide : analyse du code pour C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez améliorer la qualité de votre application en exécutant l'analyse de code de manière régulière sur le code C ou C++. Cela peut vous aider à rechercher les problèmes courants, les violations d'une bonne pratique de programmation ou les défauts difficiles à détecter à travers des tests. Les avertissements de l'analyse du code diffèrent des erreurs et des avertissements du compilateur, car l'analyse du code recherche des modèles de code spécifiques qui sont valides, mais qui peuvent créer des problèmes pour vous ou d'autres utilisateurs de votre code.  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
  
- [Configurer des ensembles de règles pour un projet](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Exécuter l'analyse du code](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analyser et résoudre les avertissements d'analyse du code](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Suppression des avertissements de l’analyse du code](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Créer des éléments de travail pour les avertissements d'analyse du code](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Explorer et filtrer les résultats d’analyse du code](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="configure-rule-sets-for-a-project"></a><a name="BKMK_ConfigureRuleSets"></a> Configurer des ensembles de règles pour un projet  
  
1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nom du projet, puis choisissez **Propriétés**.  
  
2. Les étapes suivantes sont facultatives :  
  
    1. Dans les listes **configuration** et **plateforme** , choisissez la configuration de build et la plateforme cible.  
  
    2. Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez la case à cocher **Supprimer les résultats du code généré** .  
  
        > [!NOTE]
        > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.  
  
3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, activez la case à cocher **activer l’analyse du code pour C/C++ sur la build** . Vous pouvez également exécuter l’analyse du code manuellement en ouvrant le menu **analyser** , puis en sélectionnant **exécuter l’analyse du code sur** *ProjectName*.  
  
4. Dans la liste **exécuter cet ensemble de règles** , effectuez l’une des opérations suivantes :  
  
    - Choisissez l'ensemble de règles que vous souhaitez utiliser.  
  
    - Choisissez **\<Browse...>** de spécifier un ensemble de règles personnalisé existant qui ne figure pas dans la liste.  
  
    - Définissez un ensemble de règles personnalisé.  
  
         Pour plus d’informations, consultez [création d’ensembles de règles personnalisées](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Ensembles de règles standard C/C++  
 Visual Studio inclut deux ensembles de règles standard pour le code natif :  
  
|Ensemble de règles|Description|  
|--------------|-----------------|  
|Règles minimales recommandées par Microsoft pour les projets natifs|Cet ensemble de règles couvre les problèmes les plus critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|  
|Règles recommandées natives Microsoft|Cet ensemble de règles couvre une large gamme de problèmes. Il inclut toutes les règles dans l'ensemble Règles minimales recommandées par Microsoft pour les projets natifs.|  
  
## <a name="run-code-analysis"></a><a name="BKMK_Run"></a> Exécuter l’analyse du code  
 Dans la page Analyse du code des pages de propriétés du projet, vous pouvez configurer l'analyse du code pour l'exécuter chaque fois que vous générez votre projet. Vous pouvez également exécuter l'analyse du code manuellement.  
  
 Pour exécuter l'analyse du code sur une solution :  
  
- Dans le menu **Générer**, choisissez **Exécuter l’analyse du code sur la solution**.  
  
  Pour exécuter l'analyse du code sur un projet :  
  
- Dans l'Explorateur de solutions, choisissez le nom du projet.  
  
- Dans le menu **générer** , choisissez **exécuter l’analyse du code sur le nom du** *projet*.  
  
  Le projet ou la solution est compilé et l'analyse du code est exécutée. Les résultats s'affichent dans la fenêtre Analyse du code.  
  
## <a name="analyze-and-resolve-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analyser et résoudre les avertissements d’analyse du code  
 Pour analyser un avertissement spécifique, choisissez le titre de l'avertissement dans la fenêtre Analyse du code. L'avertissement se développe pour afficher des informations supplémentaires sur le problème. Dans la mesure du possible, l'analyse du code affiche les numéros de ligne et la logique d'analyse qui a conduit à l'avertissement. Pour plus d'informations sur l'avertissement, y compris les solutions possibles au problème, choisissez l'identificateur d'avertissement pour afficher la rubrique d'aide du message dans la bibliothèque MSDN.  
  
 Lorsque vous développez un avertissement, la ligne de code à l’origine de l’avertissement est mise en surbrillance dans l’éditeur de code Visual Studio.  
  
 Après avoir identifié le problème, vous pouvez le résoudre dans votre code. Relancez ensuite l'analyse du code pour vérifier que l'avertissement ne s'affiche plus dans la fenêtre Analyse du code, et que le correctif n'a pas levé de nouveaux avertissements.  
  
> [!TIP]
> Vous pouvez réexécuter l'analyse du code dans la fenêtre Analyse du code. Choisissez le bouton **analyser** et choisissez la portée de l’analyse. Vous pouvez réexécuter l'analyse sur la solution complète ou sur un projet sélectionné.  
  
## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Suppression des avertissements d’analyse du code  
 Vous pouvez décider, dans certaines situations, de ne pas corriger un avertissement de l'analyse du code. Vous pouvez décider que la résolution de l'avertissement requiert un recodage trop important par rapport à la probabilité que le problème se produise dans une implémentation réelle de votre code. Vous pouvez également estimer que l'analyse utilisée dans l'avertissement est inadéquate pour le contexte particulier. Vous pouvez supprimer des avertissements individuels afin qu'ils n'apparaissent plus dans la fenêtre Analyse du code.  
  
 Pour supprimer un avertissement :  
  
1. Si les informations détaillées ne sont pas affichées, choisissez le titre de l'avertissement pour le développer.  
  
2. Choisissez le lien **Actions** au bas de l’avertissement.  
  
3. Choisissez **supprimer le message** , puis sélectionnez **dans la source**.  
  
   La suppression d’un message insère `#pragma warning (disable:` *warningld,* `)` qui supprime l’avertissement pour la ligne de code.  
  
## <a name="creating-work-items-for-code-analysis-warnings"></a><a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Créer des éléments de travail pour les avertissements d’analyse du code  
 Vous pouvez utiliser la fonctionnalité de suivi des éléments de travail pour enregistrer les bogues à partir de Visual Studio. Pour utiliser cette fonctionnalité, vous devez vous connecter à une instance de Team Foundation Server.  
  
 **Pour créer un élément de travail pour un ou plusieurs avertissements de code C/C++**  
  
1. Dans la fenêtre Analyse du code, développez et sélectionnez les avertissements.  
  
2. Dans le menu contextuel des avertissements, choisissez **créer un élément de travail**, puis choisissez le type d’élément de travail.  
  
3. Visual Studio crée un élément de travail unique pour les avertissements sélectionnés et affiche l’élément de travail dans une fenêtre de document de l’IDE.  
  
4. Ajoutez des informations supplémentaires, puis choisissez **enregistrer l’élément de travail**.  
  
## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Recherche et filtrage des résultats de l’analyse du code  
 Vous pouvez effectuer une recherche dans de longues listes de messages d'avertissement, et vous pouvez filtrer les avertissements dans les solutions à projets multiples.  
  
1. **Pour filtrer les avertissements par titre ou ID d’avertissement**: entrez le mot clé dans la zone de texte **filtre** .  
  
2. **Pour filtrer les avertissements par projet**: dans une solution à projets multiples, choisissez un ou plusieurs projets dans la liste en haut à droite de la fenêtre analyse du code. Choisissez le nom de la solution pour afficher tous les avertissements.  
  
3. **Pour filtrer les avertissements par gravité**: par défaut, les messages d’analyse du code sont affectés d’un niveau de gravité **Avertissement**. Vous pouvez affecter la gravité d’un ou plusieurs messages en tant qu' **erreur** dans un ensemble de règles personnalisé. Choisissez **Avertissement** ou **erreur** pour afficher uniquement les messages qui sont affectés à la gravité respective. Choisissez **tous** pour afficher tous les messages.
