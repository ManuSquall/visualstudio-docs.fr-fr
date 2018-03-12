---
title: "Avertissements et erreurs | Outil de test Microsoft IntelliTest pour les développeurs | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 77f47c2d18b43c3ab08dac5fec6281892072ab36
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="warnings-and-errors"></a>Avertissements et erreurs

## <a name="warnings-and-errors-by-category"></a>Avertissements et erreurs par catégorie

* **Limites**
  * [MaxBranches dépassé](#maxbranches-exceeded)
  * [MaxConstraintSolverTime dépassé](#maxconstraintsolvertime-exceeded)
  * [MaxConditions dépassé](#maxconditions-exceeded)
  * [MaxCalls dépassé](#maxcalls-exceeded)
  * [MaxStack dépassé](#maxstack-exceeded)
  * [MaxRuns dépassé](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests dépassé](#maxrunswithoutnewtests-exceeded)<p />

* **Résolution des contraintes**
  * [Impossible de concrétiser la solution](#cannot-concretize-solution)<p />

* **Domaines**
  * [Besoin d’aide pour construire un objet](#help-construct)
  * [Besoin d’aide pour rechercher des types](#help-types)
  * [Type utilisable deviné](#usable-type-guessed)<p />

* **Exécution**
  * [Erreur inattendue lors de l’exploration](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **Instrumentation**
  * [Méthode non instrumentée appelée](#uninstrumented-method-called)
  * [Méthode externe appelée](#external-method-called)
  * [Méthode non instrumentable appelée](#uninstrumentable-method-called)
  * [Problème de testabilité](#testability-issue)
  * [Limitation](#limitation)<p />

* **Interpréteur**
  * [Non-correspondance observée au niveau des appels](#observed-call-mismatch)
  * [Valeur stockée dans un champ statique](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches dépassé

IntelliTest limite la longueur du chemin d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité évite à IntelliTest de ne plus répondre quand le programme entre dans une boucle infinie.

Chaque branche conditionnelle et inconditionnelle du code exécuté et surveillé est comptabilisée pour cette limite, y compris les branches qui ne dépendent pas des entrées du [test unitaire paramétrable](test-generation.md#parameterized-unit-testing).

Par exemple, le code suivant consomme des branches dans la limite de 100 :

```
for (int i=0; i<100; i++) { }
```

Vous pouvez modifier l’option **MaxBranches** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). L’exemple suivant supprime cette limite :

```
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Vous pouvez également définir l’option **TestExcludePathBoundsExceeded** pour indiquer à IntelliTest comment traiter ces problèmes d’une façon générale.

Dans le code de test, vous pouvez utiliser [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) pour ignorer les contraintes générées par la condition de boucle :

```
for (int i=0; 
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++) 
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime dépassé

IntelliTest utilise un [solveur de contrainte](input-generation.md#constraint-solver) pour calculer les nouvelles entrées de test. La résolution de contrainte peut être un processus très long : IntelliTest vous permet donc de configurer des limites, en particulier **MaxConstraintSolverTime**.

Pour de nombreuses applications, augmenter considérablement le délai d’expiration n’entraîne pas une meilleure couverture. La raison en est que la plupart des dépassements du délai d’expiration sont dus à des systèmes de contraintes qui n’ont pas de solution. IntelliTest peut cependant ne pas être en mesure de déterminer qu’il est incohérent sans essayer toutes les solutions possibles, ce qui aboutit à un dépassement du délai d’expiration.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions dépassé

IntelliTest limite la longueur du chemin d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité évite à IntelliTest de ne plus répondre quand le programme entre dans une boucle infinie.

Chaque branche conditionnelle qui dépend des entrées du [test unitaire paramétrable](test-generation.md#parameterized-unit-testing) est comptabilisée pour cette limite.

Par exemple, chaque chemin dans le code suivant consomme **n+1** conditions :

```
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++) 
    { ... }
}
```

Vous pouvez modifier l’option **MaxConditions** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). Exemple :

```
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Vous pouvez également définir l’option **TestExcludePathBoundsExceeded** pour indiquer à IntelliTest comment traiter ces problèmes d’une façon générale.

Vous pouvez utiliser [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) pour ignorer les contraintes générées par la condition de boucle :

```
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)  
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls dépassé

IntelliTest limite la longueur du chemin d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité évite à IntelliTest de ne plus répondre quand le programme entre dans une boucle infinie.

Chaque appel (direct, indirect, virtuel ou de saut) du code exécuté et surveillé est comptabilisé pour cette limite.

Vous pouvez modifier l’option **MaxCalls** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). L’exemple suivant supprime cette limite :

```
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Vous pouvez également définir l’option **TestExcludePathBoundsExceeded** pour indiquer à IntelliTest comment traiter ces problèmes d’une façon générale.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack dépassé

IntelliTest limite la longueur de la pile des appels des chemins d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité évite à IntelliTest de se terminer quand un dépassement de capacité de la pile se produit.

Vous pouvez modifier l’option **MaxStack** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). L’exemple suivant supprime cette limite (ceci n’est pas recommandé) :

```
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Vous pouvez également définir l’option **TestExcludePathBoundsExceeded** pour indiquer à IntelliTest comment traiter ces problèmes d’une façon générale.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns dépassé

IntelliTest limite le nombre de chemins d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité garantit qu’IntelliTest se termine quand le programme a des boucles ou une récursivité.

Il est possible qu’IntelliTest ne produise pas un nouveau cas de test chaque fois qu’il exécute le test paramétrable avec des entrées particulières. Pour plus d’informations, consultez [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Vous pouvez modifier l’option **MaxRuns** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). L’exemple suivant supprime cette limite (ceci n’est pas recommandé) :

```
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests dépassé

IntelliTest limite le nombre de chemins d’exécution qu’il explore pendant la [génération des entrées](input-generation.md). Cette fonctionnalité garantit qu’IntelliTest se termine quand le programme a des boucles ou une récursivité.

Il est possible qu’IntelliTest ne produise pas un nouveau cas de test chaque fois qu’il exécute le test paramétrable avec des entrées particulières. Pour plus d’informations, consultez [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Alors qu’IntelliTest trouve souvent initialement de nombreuses entrées de test intéressantes, il est possible qu’après un certain temps, il ne produise plus de tests. Cette option détermine la durée pendant laquelle IntelliTest peut essayer de trouver une autre entrée de test pertinente.

Vous pouvez modifier l’option **MaxRunsWithoutNewTests** d’un attribut dérivé de **PexSettingsAttributeBase**, comme [PexClass](attribute-glossary.md#pexclass) ou [PexMethod](attribute-glossary.md#pexmethod). L’exemple suivant supprime cette limite (ceci n’est pas recommandé) :

```
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Impossible de concrétiser la solution

Cette erreur est souvent la conséquence d’une erreur antérieure. IntelliTest utilise un [solveur de contrainte](input-generation.md#constraint-solver) pour déterminer les nouvelles entrées de test. Parfois, les entrées de test proposées par le [solveur de contrainte](input-generation.md#constraint-solver) ne sont pas valides. Ceci peut se produire quand :

* Certaines contraintes ne sont pas connues.
* Si des valeurs sont créées d’une façon définie par l’utilisateur, entraînant des erreurs dans le code utilisateur.
* Certains des types impliqués ont une logique d’initialisation non contrôlée par IntelliTest (par exemple des classes COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Besoin d’aide pour construire l’objet

IntelliTest [génère des entrées de test](input-generation.md) et certaines entrées peuvent être des objets avec des champs. Ici, IntelliTest tente de générer une instance d’une classe qui a un champ privé, et il part du principe qu’un comportement intéressant du programme se produit quand ce champ privé a une valeur particulière. 

Cependant, si cela est possible avec la réflexion, IntelliTest ne fabrique pas d’objets avec des valeurs de champ arbitraires. Au lieu de cela, dans ces situations, il s’appuie sur les indications données par l’utilisateur sur la façon d’utiliser les méthodes publiques d’une classe pour créer un objet et pour le placer dans un état où son champ privé a la valeur souhaitée.

Pour découvrir comment vous pouvez aider IntelliTest à construire des objets intéressants, consultez [Instanciation de classes existantes](input-generation.md#existing-classes). 

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Besoin d’aide pour rechercher des types

IntelliTest [génère des entrées de test](input-generation.md) pour tous les types .NET. Ici, IntelliTest tente de créer une instance qui dérive d’une classe abstraite ou qui implémente une interface abstraite, et il n’a connaissance d’aucun type satisfaisant les contraintes. 

Vous pouvez aider IntelliTest en pointant vers un ou plusieurs types qui correspondent aux contraintes. Un des attributs suivants peut généralement aider :

* **PexUseTypeAttribute**, qui pointe vers un type particulier.

  Par exemple, si IntelliTest indique qu’il « ne connaît aucun type pouvant être assigné à **System.Collections.IDictionary**», vous pouvez l’aider en attachant le **PexUseTypeAttribute** suivant au test (ou à la classe d’attachement) :

  ```
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Un attribut de niveau assembly**

  ```
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Type utilisable deviné

IntelliTest [génère des entrées de test](input-generation.md) pour tous les types .NET. Quand un type est abstrait ou est une interface, IntelliTest doit choisir une implémentation particulière de ce type. Pour faire ce choix, il a besoin de savoir quels types existent. 

Quand cet avertissement est affiché, il indique qu’IntelliTest a recherché dans certains des assemblys référencés et a trouvé un type d’implémentation, mais qu’il n’est pas certain de devoir utiliser ce type ou qu’il existe des types plus appropriés disponibles ailleurs. IntelliTest a simplement choisi un type qui semblait prometteur.

Pour éviter cet avertissement, vous pouvez accepter le choix de type d’IntelliTest ou bien l’aider à utiliser d’autres types en ajoutant un [PexUseType](attribute-glossary.md#pexusetype) correspondant.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Erreur inattendue pendant l’exploration

Une exception inattendue a été interceptée lors de l’exploration d’un test.

Merci de [signaler ceci comme bogue](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Une exception s’est produite dans le code utilisateur. Inspectez la trace de la pile et supprimez le bogue dans votre code.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Méthode non instrumentée appelée

IntelliTest [génère des entrées de test](input-generation.md) en surveillant l’exécution du programme. Il est essentiel que le code concerné soit correctement instrumenté pour qu’IntelliTest puisse surveiller son comportement.

Cet avertissement apparaît quand le code instrumenté appelle des méthodes dans un autre assembly non instrumenté. Si vous voulez qu’IntelliTest explore l’interaction entre les deux, vous devez aussi instrumenter l’autre assembly (ou des parties de celui-ci).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Méthode externe appelée

IntelliTest [génère des entrées de test](input-generation.md) en surveillant l’exécution d’applications .NET. IntelliTest ne peut pas générer des entrées de test significatives pour du code qui n’est pas écrit dans un langage .NET.

Cet avertissement apparaît quand le code instrumenté appelle une méthode native non managée qu’IntelliTest ne peut pas analyser. Si vous voulez qu’IntelliTest explore l’interaction entre les deux, vous devez simuler la méthode non managée.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Méthode non instrumentable appelée

IntelliTest [génère des entrées de test](input-generation.md) en surveillant l’exécution d’applications .NET. Il existe cependant certaines méthodes que, pour des raisons techniques, IntelliTest ne peut pas surveiller. Par exemple, IntelliTest ne peut pas surveiller un constructeur statique.

Cet avertissement apparaît quand le code instrumenté appelle une méthode qu’IntelliTest ne peut pas surveiller. 

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problème de testabilité

IntelliTest [génère des entrées de test](input-generation.md) en surveillant l’exécution du programme. Il peut générer des entrées de test appropriées seulement quand le programme est déterministe et quand le comportement approprié est contrôlé par les entrées de test.

Cet avertissement apparaît parce que, pendant l’exécution de votre cas de test, une méthode qui a été appelée se comporte de façon non déterministe ou interagit avec l’environnement. **System.Random** et **System.IO.File** sont des exemples de méthodes. Si vous voulez qu’IntelliTest crée des entrées de test significatives, vous devez simuler les méthodes signalées par IntelliTest comme posant des problèmes de testabilité.

<a name="limitation"></a>
## <a name="limitation"></a>Limitation

IntelliTest [génère les entrées de test](input-generation.md) en utilisant un [solveur de contrainte](input-generation.md#constraint-solver).
Certaines opérations sont cependant au-delà de l’étendue du [solveur de contrainte](input-generation.md#constraint-solver).
Ceci inclut actuellement :

* La plupart des opérations à virgule flottante (seules certaines opérations arithmétiques linéaires sont prises en charge sur les nombres à virgule flottante).
* Les conversions entre les nombres à virgule flottante et les entiers.
* Toutes les opérations sur le type **System.Decimal**.

Cet avertissement apparaît quand le code exécuté effectue une opération ou appelle une méthode qu’IntelliTest ne peut pas interpréter. 

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Non-correspondance observée au niveau des appels

IntelliTest [génère des entrées de test](input-generation.md) en surveillant l’exécution du programme. IntelliTest peut cependant ne pas être en mesure de surveiller toutes les instructions. Par exemple, il ne peut pas surveiller du code natif ni du code qui n’est pas instrumenté.

Quand IntelliTest surveille le code, il ne peut pas générer des entrées de test appropriées pour ce code.
Souvent, IntelliTest ignore qu’il ne peut pas surveiller une méthode jusqu’au retour d’un appel à cette méthode. Cependant, la cause de cet avertissement est :

* IntelliTest a surveillé du code, qui a lancé un appel à une méthode non instrumentée.
* La méthode non instrumentée a appelé une méthode qui est instrumentée.
* IntelliTest surveille la méthode instrumentée qui a été appelée. 

IntelliTest ne sait pas ce qu’a fait la méthode intermédiaire non instrumentée et il risque de ne pas pouvoir générer des entrées de test qui sont pertinentes pour l’appel instrumenté imbriqué.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Valeur stockée dans un champ statique

IntelliTest peut déterminer systématiquement [les entrées de test pertinentes](input-generation.md) seulement quand le test unitaire est déterministe ; en d’autres termes, il se comporte toujours de la même façon pour les mêmes entrées de test. En particulier, cela signifie que le test doit laisser le système dans un état qui permet de réexécuter ce test.
Dans l’idéal, le test unitaire ne doit changer aucun état global, mais toutes les interactions avec les éléments globaux doivent être simulées.

Cet avertissement indique qu’un champ statique a été modifié : ceci risque de faire que le test se comporte de façon non déterministe.

Dans certains cas, la modification d’un champ statique est acceptable :

* Quand les entrées de test font que le code de configuration ou de nettoyage annule la modification.
* Quand le champ est initialisé une seule fois et que sa valeur ne change pas par la suite

<a name="report-bug"></a>

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
