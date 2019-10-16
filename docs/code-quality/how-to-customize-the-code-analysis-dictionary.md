---
title: 'Comment : personnaliser le dictionnaire d’analyse du code'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4a6c94f5784d57a90dd31f21f8829b3141140d0
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349589"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Comment : personnaliser le dictionnaire d’analyse du code

L’analyse du code utilise un dictionnaire intégré pour vérifier les identificateurs dans votre code en vue d’identifier les erreurs de l’orthographe, de la grammaire et d’autres conventions de nommage des règles de conception .NET. Vous pouvez créer un fichier XML de dictionnaire personnalisé pour ajouter, supprimer ou modifier des termes, des abréviations et des acronymes du dictionnaire intégré.

Par exemple, supposons que votre code contenait une classe nommée **DoorKnokker**. L’analyse du code identifie le nom comme un composé de deux mots : **porte** et **knokker**. Il déclenche alors un avertissement indiquant que **knokker** n’a pas été correctement orthographié. Pour forcer l’analyse du code à reconnaître l’orthographe, vous pouvez ajouter le terme **knokker** au dictionnaire personnalisé.

## <a name="to-create-a-custom-dictionary"></a>Pour créer un dictionnaire personnalisé

Créez un fichier nommé **CustomDictionary. xml**.

Définissez vos mots personnalisés à l’aide de la structure XML suivante :

```xml
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

## <a name="custom-dictionary-elements"></a>Éléments de dictionnaire personnalisé

Vous pouvez modifier le comportement du dictionnaire d’analyse du code en ajoutant des termes comme texte interne des éléments suivants dans le dictionnaire personnalisé :

- [Dictionnaire/mots/reconnus/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dictionnaire/mots/non reconnu/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/Deprecated/term [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionnaire/mots/composé/terme [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionnaire/Acronyms/CasingExceptions/acronyme](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a>Dictionnaire/mots/reconnus/Word

Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme correctement orthographié, ajoutez le terme comme texte interne d’un élément Dictionary/Words/recognized/Word. Les termes du dictionnaire/des mots/reconnus/Word ne respectent pas la casse.

**Exemple**

```xml
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

Les termes du dictionnaire/des mots/nœuds reconnus sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Dictionnaire/mots/non reconnu/Word

Pour exclure un terme de la liste des termes que l’analyse du code identifie comme étant correctement orthographiés, ajoutez le terme à exclure comme texte interne d’un élément Dictionary/Words/non reconnu/Word. Les termes du dictionnaire/des mots/non reconnus/les éléments Word ne respectent pas la casse.

**Exemple**

```xml
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

Les termes du nœud dictionnaire/mots/non reconnus sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Dictionary/Words/Deprecated/term [@PreferredAlternate]

Pour inclure un terme dans la liste des termes identifié par l’analyse du code comme étant déconseillé, ajoutez le terme comme texte interne d’un élément Dictionary/Words/Deprecated/term. Un terme déconseillé est un mot qui est correctement orthographié, mais qui ne doit pas être utilisé.

Pour inclure un autre terme suggéré dans l’avertissement, spécifiez le remplacement dans l’attribut PreferredAlternate de l’élément term. Vous pouvez laisser la valeur d’attribut vide si vous ne souhaitez pas suggérer une alternative.

- Le terme déconseillé dans l’élément Dictionary/Words/Deprecated/term ne respecte pas la casse.

- La valeur de l’attribut PreferredAlternate est sensible à la casse. Utilisez la casse Pascal pour les substituts composés.

**Exemple**

```xml
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

Les termes du nœud dictionnaire/mots/déconseillé sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Dictionnaire/mots/composé/terme [@CompoundAlternate]

Le dictionnaire intégré identifie certains termes comme des termes simples et discrets plutôt qu’un terme composé. Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme un mot composé et pour spécifier la casse correcte du terme, ajoutez le terme comme texte interne d’un élément Dictionary/Words/Compound-term. Dans l’attribut CompoundAlternate de l’élément term, spécifiez les mots individuels qui composent le terme composé en majuscules la première lettre des mots individuels (casse Pascal). Notez que le terme spécifié dans le texte interne est automatiquement ajouté à la liste Dictionary/Words/DiscreteExceptions.

- Le terme composé dans l’élément Dictionary/Words/Compound/term ne respecte pas la casse.

- La valeur de l’attribut CompoundAlternate est sensible à la casse. Utilisez la casse Pascal pour les substituts composés.

**Exemple**

```xml
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

Les termes du nœud Dictionary/Words/Compound sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Dictionary/Words/DiscreteExceptions/Term

Pour exclure un terme dans la liste des termes que l’analyse du code identifie comme un mot unique et discret lorsque le terme est vérifié par les règles de casse des mots composés, ajoutez le terme comme texte interne d’un élément Dictionary/Words/DiscreteExceptions/Term. Le terme dans l’élément Dictionary/Words/DiscreteExceptions/Term ne respecte pas la casse.

**Exemple**

```xml
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

Les termes du nœud Dictionary/Words/DiscreteExceptions sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Dictionnaire/Acronyms/CasingExceptions/acronyme

Pour inclure un acronyme dans la liste des termes que l’analyse du code identifie comme correctement orthographiés et pour indiquer comment l’acronyme est vérifié par les règles de casse des mots composés, ajoutez le terme comme texte interne d’un dictionnaire/Acronyms/CasingExceptions/ Acronyme, élément. L’acronyme dans l’élément Dictionary/acronymes/CasingExceptions/acronyme respecte la casse.

**Exemple**

```xml
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

Les termes du nœud dictionary/acronymes/CasingExceptions sont appliqués aux règles d’analyse de code suivantes :

- [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Pour appliquer un dictionnaire personnalisé à un projet

1. Dans **Explorateur de solutions**, utilisez l’une des procédures suivantes :

2. Pour ajouter un dictionnaire à un seul projet, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter un élément existant**. Spécifiez le fichier dans la boîte de dialogue **Ajouter un élément existant** .

3. Pour ajouter un dictionnaire partagé entre plusieurs projets, localisez le fichier à partager dans la boîte de dialogue **Ajouter un élément existant** , cliquez sur la flèche vers le bas du bouton **Ajouter** , puis cliquez sur **Ajouter en tant que lien**.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du fichier **CustomDictionary. xml** , puis cliquez sur **Propriétés**.

5. Dans la liste **action de génération** , sélectionnez **CodeAnalysisDictionary**.

6. Dans la liste **copier dans le répertoire de sortie** , sélectionnez **ne pas copier**.
