---
title: 'Procédure pas à pas : Test en premier la prise en charge avec l’utilisation de la fonctionnalité Générer à partir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2308be73eb7b483168544dc706a9b682af7eca35
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755136"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>Procédure pas à pas : prise en charge du développement basé d’abord sur les tests avec la fonctionnalité Générer à partir de l’utilisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique montre comment utiliser la fonctionnalité [Générer à partir de l’utilisation](../misc/generate-from-usage.md), qui prend en charge le développement basé d’abord sur les tests.  
  
 Le*développement basé d’abord sur les tests* est une approche de conception logicielle dans laquelle vous écrivez d’abord des tests unitaires basés sur des spécifications de produits, puis vous écrivez le code source nécessaire pour que les tests réussissent. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prend en charge le développement basé d’abord sur les tests en générant de nouveaux types et membres dans le code source lorsque vous y faites référence pour la première fois dans vos cas de test, avant de les définir.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] génère les nouveaux types et membres avec une interruption minimale de votre flux de travail. Vous pouvez créer des stubs pour des types, méthodes, propriétés, champs ou constructeurs sans quitter votre emplacement actuel dans le code. Quand vous ouvrez une boîte de dialogue pour spécifier des options de génération de type, le fichier ouvert actuellement récupère immédiatement le focus lorsque la boîte de dialogue se ferme.  
  
 Vous pouvez utiliser la fonctionnalité Générer à partir de l’utilisation avec les infrastructures de test qui s’intègrent à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dans cette rubrique, nous allons utiliser l’infrastructure de test unitaire Microsoft.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Pour créer un projet de bibliothèque de classes Windows et un projet de test  
  
1.  Dans [!INCLUDE[csprcs](../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], créez un projet de bibliothèque de classes Windows. Nommez-le `GFUDemo_VB` ou `GFUDemo_CS`, selon le langage que vous utilisez.  
  
2.  Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur l’icône de solution en haut, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet** , dans le volet **Types de projets** à gauche, cliquez sur **Test**.  
  
3.  Dans le volet **Modèles** , cliquez sur **Projet de test unitaire** et acceptez le nom par défaut UnitTestProject1. L’illustration suivante montre la boîte de dialogue quand elle apparaît dans [!INCLUDE[csprcs](../includes/csprcs-md.md)]. Dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], la boîte de dialogue a une apparence similaire.  
  
     ![Boîte de dialogue Nouveau projet de test](../ide/media/newproject-test.png "NewProject_Test")  
Boîte de dialogue Nouveau projet de test  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Nouveau projet** .

5.  Dans votre projet de classe, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis cliquez sur **Ajouter une référence**.

6.  Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **Projets**, puis sélectionnez votre projet de test unitaire.

7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire de références**.

8.  Dans le fichier **Class1**, immédiatement après la toute dernière instruction **using**, ajoutez une instruction **using** pour le projet de test :

    * En Visual Basic, ajoutez `Using UnitTestProject1`
    
    * En C#, ajoutez `using UnitTestProject1;`
    
9.  Enregistrez votre solution. Vous êtes maintenant prêt à commencer l’écriture des tests.  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>Pour générer une nouvelle classe à partir d’un test unitaire  
  
1.  Le projet de test contient un fichier nommé UnitTest1. Double-cliquez sur ce fichier dans l’ **Explorateur de solutions** pour l’ouvrir dans l’éditeur de code. Une classe de test et une méthode de test ont été générées.  
  
2.  Recherchez la déclaration de classe `UnitTest1` et renommez-la `AutomobileTest`. En C#, si un constructeur `UnitTest1()` est présent, renommez-le `AutomobileTest()`.  
  
    > [!NOTE]
    >  IntelliSense offre désormais deux options pour la saisie semi-automatique des instructions IntelliSense : le *mode de saisie semi-automatique* et le *mode de suggestion*. Utilisez le mode de suggestion quand les classes et les membres sont utilisés avant d’être définis. Quand une fenêtre IntelliSense est ouverte, vous pouvez appuyer sur Ctrl+Alt+Espace pour basculer entre le mode de saisie semi-automatique et le mode de suggestion. Pour plus d'informations, voir [Using IntelliSense](../ide/using-intellisense.md) . Le mode de suggestion sera utile lorsque vous taperez `Automobile` à l’étape suivante.  
  
3.  Recherchez la méthode `TestMethod1()` et renommez-la `DefaultAutomobileIsInitializedCorrectly()`. Dans cette méthode, créez une instance d’une classe nommée `Automobile`, comme indiqué dans les illustrations suivantes. Un soulignement ondulé indique une erreur de compilation et une balise active apparaît sous le nom de type. L’emplacement exact de la balise active varie selon que vous utilisez [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
     ![Soulignement d’étiquette active en Visual Basic](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB")  
Visual Basic  
  
     ![Soulignement d’étiquette active en C&#35;](../ide/media/genclass-underline.png "GenClass_Underline")  
Visual C#  
  
4.  Placez le pointeur de la souris sur la balise active pour afficher un message d’erreur indiquant qu’aucun type nommé `Automobile` n’est encore défini. Cliquez sur la balise active ou appuyez sur Ctrl+. (Ctrl+point) pour ouvrir le menu contextuel Générer à partir de l’utilisation, comme indiqué dans les illustrations suivantes.  
  
     ![Menu contextuel de l’étiquette en Visual Basic](../ide/media/genclass-smartvb.png "GenClass_SmartVB")  
Visual Basic  
  
     ![Menu contextuel de l’étiquette en C&#35;](../ide/media/genclass-smartcs.png "GenClass_SmartCS")  
Visual C#  
  
5.  Vous avez maintenant deux choix : Vous pouvez cliquer sur **Générer 'Class Automobile'** pour créer un fichier dans votre projet de test et le remplir avec une classe vide nommée `Automobile`. C’est un moyen rapide de créer une classe dans un nouveau fichier qui a des modificateurs d’accès par défaut dans le projet actuel. Vous pouvez également cliquer sur **Générer un nouveau type** pour ouvrir la boîte de dialogue **Générer un nouveau type** . Elle vous permet entre autres de placer la classe dans un fichier existant et d’ajouter le fichier à un autre projet.  
  
     Cliquez sur **Générer un nouveau type** pour ouvrir la boîte de dialogue **Générer un nouveau type** , illustrée ci-dessous. Dans la liste **Projet** , cliquez sur **GFUDemo_VB** ou **GFUDemo_CS** pour que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ajoute le fichier au projet de code source plutôt qu’au projet de test.  
  
     ![Boîte de dialogue Générer un nouveau type](../ide/media/genotherdialog.png "GenOtherDialog")  
Boîte de dialogue Générer un nouveau type  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue et créer le fichier.  
  
7.  Dans l’ **Explorateur de solutions**, regardez sous le nœud du projet GFUDemo_VB ou GFUDemo_CS pour vérifier que le nouveau fichier Automobile.vb ou Automobile.cs existe. Dans l’éditeur de code, le focus est toujours dans `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. Vous pouvez continuer à écrire votre test avec un minimum d’interruption.  
  
### <a name="to-generate-a-property-stub"></a>Pour générer un stub de propriété  
  
1.  Supposez que la spécification de produit indique que la classe `Automobile` a deux propriétés publiques nommées `Model` et `TopSpeed`. Ces propriétés doivent être initialisées avec les valeurs par défaut `"Not specified"` et `-1` par le constructeur par défaut. Le test unitaire suivant vérifie que le constructeur par défaut affecte les valeurs par défaut correctes aux propriétés.  
  
     Ajoutez la ligne de code suivante à `DefaultAutomobileIsInitializedCorrectly`.  
  
     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]  
  
     Comme le code fait référence à deux propriétés non définies sur `Automobile`, une balise active apparaît. Cliquez sur la balise active pour `Model` , puis sur **Générer le stub de propriété**. Générez aussi un stub de propriété pour la propriété `TopSpeed` .  
  
     Dans la classe `Automobile` , les types des nouvelles propriétés sont correctement déduits du contexte.  
  
     L’illustration suivante montre le menu contextuel de la balise active.  
  
     ![Menu contextuel Générer la propriété en Visual Basic](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB")  
Visual Basic  
  
     ![Menu contextuel Générer la propriété en C&#35;](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS")  
Visual C#  
  
### <a name="to-locate-the-source-code"></a>Pour rechercher le code source  
  
1.  Utilisez la fonctionnalité **Naviguer vers** pour accéder au fichier de code source Automobile.cs ou Automobile.vb et vérifier que les nouvelles propriétés ont été générées.  
  
     La fonctionnalité **Naviguer vers** vous permet d’entrer rapidement une chaîne de texte, telle qu’un nom de type ou une partie d’un nom, et d’accéder à l’emplacement souhaité en cliquant sur l’élément dans la liste des résultats.  
  
     Ouvrez la boîte de dialogue **Naviguer vers** en cliquant sur l’éditeur de code et en appuyant sur Ctrl+, (Ctrl+virgule). Dans la zone de texte, tapez `automobile`. Cliquez sur la classe **Automobile** dans la liste, puis cliquez sur **OK**.  
  
     La fenêtre **Naviguer vers** est illustrée ci-dessous.  
  
     ![Boîte de dialogue Naviguer vers](../ide/media/navigate-2.png "Navigate_2")  
Fenêtre Naviguer vers  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>Pour générer un stub pour un nouveau constructeur  
  
1.  Dans cette méthode de test, vous allez générer un stub de constructeur qui initialisera les propriétés `Model` et `TopSpeed` pour qu’elles aient les valeurs que vous spécifiez. Plus tard, vous ajouterez du code pour terminer le test. Ajoutez la méthode de test supplémentaire suivante à votre classe `AutomobileTest` .  
  
     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]  
  
2.  Cliquez sur la balise active sous le nouveau constructeur de classe, puis sur **Générer le stub de constructeur**. Dans le fichier de classe `Automobile` , notez que le nouveau constructeur a examiné les noms des variables locales utilisées dans l’appel de constructeur, qu’il a identifié des propriétés ayant le même nom dans la classe `Automobile` et qu’il a fourni du code dans le corps du constructeur pour stocker les valeurs d’arguments dans les propriétés `Model` et `TopSpeed` . (Dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], les champs `_model` et `_topSpeed` dans le nouveau constructeur sont les champs de stockage définis implicitement pour les propriétés `Model` et `TopSpeed` .)  
  
3.  Une fois le nouveau constructeur généré, une ligne ondulée apparaît sous l’appel au constructeur par défaut dans `DefaultAutomobileIsInitializedCorrectly`. Le message d’erreur indique que la classe `Automobile` n’a aucun constructeur qui n’accepte aucun argument. Pour générer un constructeur explicite par défaut qui n’a aucun paramètre, cliquez sur la balise active, puis sur **Générer le stub de constructeur**.  
  
### <a name="to-generate-a-stub-for-a-method"></a>Pour générer un stub pour une méthode  
  
1.  Supposez que la spécification stipule qu’un nouveau `Automobile` peut être placé à l’état En cours d’exécution si ses propriétés `Model` et `TopSpeed` ont des valeurs autres que les valeurs par défaut. Ajoutez les lignes suivantes à la méthode `AutomobileWithModelNameCanStart` .  
  
     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]  
  
2.  Cliquez sur la balise active pour l’appel de méthode `myAuto.Start` , puis sur **Générer un stub de méthode**.  
  
3.  Cliquez sur la balise active pour la propriété `IsRunning` , puis sur **Générer le stub de propriété**. La classe `Automobile` contient maintenant le code suivant.  
  
     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]  
  
### <a name="to-run-the-tests"></a>Pour exécuter les tests  
  
1.  Dans le menu **Test unitaire** , pointez sur **Exécuter les tests unitaires**, puis cliquez sur **Tous les tests**. Cette commande exécute tous les tests dans toutes les infrastructures de test écrits pour la solution actuelle.  
  
     Il y a ici deux tests, qui échouent comme prévu. Le test `DefaultAutomobileIsInitializedCorrectly` échoue car la condition `Assert.IsTrue` retourne `False`. Le test `AutomobileWithModelNameCanStart` échoue car la méthode `Start` dans la classe `Automobile` lève une exception.  
  
     La fenêtre **Résultats des tests** est illustrée ci-dessous.  
  
     ![Résultats des tests qui ont échoué](../ide/media/testsfailed.png "TestsFailed")  
Fenêtre Résultats des tests  
  
2.  Dans la fenêtre **Résultats des tests** , double-cliquez sur chaque ligne de résultat de test pour accéder à l’emplacement de chaque échec de test.  
  
### <a name="to-implement-the-source-code"></a>Pour implémenter le code source  
  
1.  Ajoutez le code suivant au constructeur par défaut pour que les propriétés `Model`, `TopSpeed` et `IsRunning` soient toutes initialisées à leurs valeurs par défaut `"Not specified"`, `-1`, et `True` (`true`).  
  
     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]  
  
2.  Quand la méthode `Start` est appelée, elle doit affecter la valeur true à l’indicateur `IsRunning` uniquement si les propriétés `Model` ou `TopSpeed` ont des valeurs autres que leurs valeurs par défaut. Supprimez `NotImplementedException` du corps de la méthode et ajoutez le code suivant.  
  
     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]  
  
### <a name="to-run-the-tests-again"></a>Pour réexécuter les tests  
  
1.  Dans le menu **Test** , pointez sur **Exécuter**, puis cliquez sur **Tous les tests de la solution**. Cette fois-ci, les tests réussissent. La fenêtre **Résultats des tests** est illustrée ci-dessous.  
  
     ![Résultats des tests qui ont réussi](../ide/media/testspassed.png "TestsPassed")  
Fenêtre Résultats des tests  
  
## <a name="see-also"></a>Voir aussi  
 [Générer à partir de l’utilisation](../misc/generate-from-usage.md)   
 [Écriture de code](../ide/writing-code-in-the-code-and-text-editor.md)   
 [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)   
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)
