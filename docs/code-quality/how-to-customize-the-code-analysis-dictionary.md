---
title: 'Comment : personnaliser le dictionnaire d’analyse du code'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1a0ecc19d5648d6ee9454a53c9b0a1ebcb5a2e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Comment : personnaliser le dictionnaire d’analyse du code
Analyse du code utilise un dictionnaire intégré pour vérifier les identificateurs dans votre code pour les erreurs dans l’orthographe et grammaire cas autres conventions d’affectation de noms de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] des recommandations. Vous pouvez créer un fichier Xml de dictionnaire personnalisé pour ajouter, supprimer ou modifier les termes et abréviations acronymes au dictionnaire intégré.

 Par exemple, supposons que votre code contenue une classe nommée **DoorKnokker (heurtoire)**. Analyse du code identifie le nom comme composé de deux mots : **porte** et **knokker**. Elle déclencherait ensuite un avertissement qui **knokker** n’est pas correctement orthographié. Pour forcer l’analyse du code à reconnaître l’orthographe, vous pouvez ajouter le terme **knokker** au dictionnaire.

## <a name="to-create-a-custom-dictionary"></a>Pour créer un dictionnaire personnalisé
 Créer un fichier nommé **CustomDictionary.xml**.

 Définissez vos mots personnalisés à l’aide de la structure XML suivante :

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Éléments du dictionnaire personnalisé
 Vous pouvez modifier le comportement du dictionnaire d’analyse du Code en ajoutant des termes comme texte interne des éléments suivants dans le dictionnaire personnalisé :

-   [Dictionnaire/mots/reconnu/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

-   [Dictionnaire/mots/non reconnue/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

-   [Dictionnaire/mots/déconseillée/Term [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

-   [Dictionary/Words/Compound/Term [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

-   [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

-   [Dictionnaire/acronymes/CasingExceptions/acronyme](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionnaire/mots/reconnu/Word
 Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme correctement orthographié, ajoutez ce terme comme texte interne d’un élément Dictionary/Words/reconnaît/Word. Termes du contrat dans les éléments du dictionnaire/mots/reconnaît/Word ne respectent pas la casse.

 **Exemple**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Les conditions dans les nœuds de dictionnaire/mots/reconnues s’appliquent aux règles d’analyse du code suivant :

-   [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionnaire/mots/non reconnue/Word
 Pour exclure un terme de la liste des termes que l’analyse du code identifie comme correctement orthographié, ajoutez ce terme à exclure en tant que le texte interne d’un élément Dictionary/Words/non reconnu/Word. Termes du contrat dans les éléments du dictionnaire/mots/non reconnu/Word ne respectent pas la casse.

 **Exemple**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Les conditions dans le nœud de dictionnaire/mots/non reconnu s’appliquent aux règles d’analyse du code suivant :

-   [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionnaire/mots/déconseillée/Term [@PreferredAlternate]
 Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme déconseillés, ajoutez ce terme comme texte interne d’un élément Dictionary/Words/Deprecated/Term. Un terme déconseillé est un mot qui est correctement orthographié, mais ne doit pas être utilisé.

 Pour inclure un autre terme suggéré dans l’avertissement, spécifiez l’autre dans l’attribut PreferredAlternate de l’élément du terme. Vous pouvez laisser la valeur d’attribut vide si vous ne souhaitez pas proposer une solution de remplacement.

-   Le terme déconseillé dictionnaire/mots/élément Deprecated/Term ne respecte pas la casse.

-   La valeur d’attribut PreferredAlternate respecte la casse. Utilisez la casse Pascal pour les autres termes composés.

 **Exemple**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>

```

 Termes du noeud Dictionary/Words/Deprecated sont appliqués aux règles d’analyse du code suivant :

-   [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/Words/Compound/Term [@CompoundAlternate]
 Le dictionnaire intégré identifie certains termes en tant que termes uniques, discrets, plutôt qu’un terme composé. Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme mot composé et spécifier la casse correcte du terme, ajoutez ce terme comme texte interne d’un élément Dictionary/Words/Compound/Term. Dans l’attribut CompoundAlternate de l’élément Term, spécifiez les mots individuels qui composent le terme composé en majuscules la première lettre des mots individuels (casse Pascal). Notez que le terme spécifié dans le texte interne est automatiquement ajouté à la liste de mots/dictionnaire/DiscreteExceptions.

-   Le terme déconseillé dictionnaire/mots/élément Deprecated/Term ne respecte pas la casse.

-   La valeur d’attribut PreferredAlternate respecte la casse. Utilisez la casse Pascal pour les autres termes composés.

 **Exemple**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>

```

 Dans le nœud de dictionnaire/mots/composée, les conditions s’appliquent aux règles d’analyse du code suivant :

-   [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term
 Pour exclure un terme dans la liste des termes que l’analyse du code identifie comme une seule, word discret lorsque le terme est vérifié par les règles de casse pour les mots composés, ajoutez ce terme comme texte interne d’un élément Dictionary/Words/DiscreteExceptions/Term. Le terme dans l’élément Dictionary/Words/DiscreteExceptions/Term ne respecte pas la casse.

 **Exemple**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>

```

 Les conditions dans le nœud de dictionnaire/mots/DiscreteExceptions s’appliquent aux règles d’analyse du code suivant :

-   [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionnaire/acronymes/CasingExceptions/acronyme
 Pour inclure un acronyme dans la liste des termes que l’analyse du code identifie comme correctement orthographié et pour indiquer le fonctionnement des règles de l’acronyme lorsque le terme est vérifié par la casse des mots composés, ajoutez ce terme comme texte interne d’un dictionnaire/acronymes/CasingExceptions / Élément Acronym. L’acronyme dans l’élément du dictionnaire/acronymes/CasingExceptions/Acronym respecte la casse.

 **Exemple**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>

```

 Les conditions dans le nœud de dictionnaire/acronymes/CasingExceptions s’appliquent aux règles d’analyse du code suivant :

-   [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Pour appliquer un dictionnaire personnalisé à un projet

1.  Dans **l’Explorateur de solutions**, utilisez une des procédures suivantes :

2.  Pour ajouter un dictionnaire dans un projet unique, cliquez sur le nom du projet, puis **ajouter un élément existant**. Spécifiez le fichier dans le **ajouter un élément existant** boîte de dialogue.

3.  Pour ajouter un dictionnaire qui est partagé entre deux ou plusieurs projets, recherchez le fichier à partager dans le **ajouter un élément existant** boîte de dialogue, cliquez sur la flèche bas sur le **ajouter** puis cliquez sur **ajouter en tant que lien** .

4.  Dans **l’Explorateur de solutions**, cliquez sur le **CustomDictionary.xml** nom de fichier et cliquez sur **propriétés**.

5.  À partir de la **Action de génération** liste, sélectionnez **CodeAnalysisDictionary**.

6.  À partir de la **copier dans le répertoire de sortie** liste, sélectionnez **ne copiez pas**.