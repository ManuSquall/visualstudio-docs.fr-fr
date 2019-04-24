---
title: 'Procédure : Personnaliser le dictionnaire d’analyse du code'
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
ms.openlocfilehash: cbc2d0f0863ae4b9083c0fb56873eb18b665c7c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081643"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Procédure : Personnaliser le dictionnaire d’analyse du code
Analyse du code utilise un dictionnaire intégré pour vérifier les identificateurs dans votre code pour les erreurs dans l’orthographe, grammaire cas et autres conventions d’affectation de noms de règles du .NET Framework. Vous pouvez créer un fichier Xml de dictionnaire personnalisé pour ajouter, supprimer ou modifier des termes, abréviations et acronymes au dictionnaire intégré.

 Par exemple, supposez que votre code contient une classe nommée **DoorKnokker (heurtoire)**. Analyse du code identifie le nom comme composé de deux mots : **porte** et **knokker**. Il déclenche alors un avertissement qui **knokker** n’est pas correctement orthographié. Pour forcer l’analyse du code pour reconnaître l’orthographe, vous pouvez ajouter le terme **knokker** au dictionnaire personnalisé.

## <a name="to-create-a-custom-dictionary"></a>Pour créer un dictionnaire personnalisé
 Créez un fichier nommé **CustomDictionary.xml**.

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
 Vous pouvez modifier le comportement du dictionnaire d’analyse du Code en ajoutant des termes du contrat en tant que le texte interne des éléments suivants dans le dictionnaire personnalisé :

- [Dictionnaire/mots/reconnu/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Dictionnaire/mots/non reconnue/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionnaire/mots/reconnu/Word
 Pour inclure un terme dans la liste de termes que l’analyse du code identifie comme correctement orthographié, ajoutez ce terme comme texte interne d’un élément de dictionnaire/mots/Recognized/Word. Termes du contrat dans les éléments du dictionnaire/mots/Recognized/Word ne respectent pas la casse.

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

 Termes mots/dictionnaire/Recognized nœuds sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : Mots composés doivent être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionnaire/mots/non reconnue/Word
 Pour exclure un terme de la liste de termes que l’analyse du code identifie comme correctement orthographié, ajoutez le terme à exclure en tant que le texte interne d’un élément de dictionnaire/mots/non reconnue/Word. Termes du contrat dans les éléments du dictionnaire/mots/non reconnue/Word ne respectent pas la casse.

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

 Termes dans le nœud de dictionnaire/mots/non reconnu sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : Mots composés doivent être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionnaire/mots/déconseillé/terme [@PreferredAlternate]
 Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme déconseillés, ajoutez ce terme comme texte interne d’un élément de dictionnaire/mots/Deprecated/Term. Un terme déconseillé est un mot qui est correctement orthographié, mais ne doit pas être utilisé.

 Pour inclure un autre terme suggéré dans l’avertissement, spécifiez l’autre dans l’attribut PreferredAlternate de l’élément de terme. Vous pouvez laisser la valeur d’attribut vide si vous ne souhaitez pas suggérer un autre terme.

- Le terme déconseillé dictionnaire/mots/élément Deprecated/Term ne respecte pas la casse.

- La valeur d’attribut PreferredAlternate respecte la casse. Utiliser la casse Pascal pour les autres termes composés.

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

 Termes du noeud Dictionary/Words/Deprecated sont appliqués aux règles d’analyse de code suivant :

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : Mots composés doivent être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionnaire/mots/Compound/Term [@CompoundAlternate]
 Le dictionnaire intégré identifie certains termes comme termes uniques, discrets, au lieu d’un terme composé. Pour inclure un terme dans la liste des termes que l’analyse du code identifie comme mot composé et spécifier la casse correcte du terme, ajoutez ce terme comme texte interne d’un élément de dictionnaire/mots/Compound/Term. Dans l’attribut CompoundAlternate de l’élément de terme, spécifiez les mots individuels qui composent le terme composé en tirant parti de la première lettre des mots individuels (casse Pascal). Notez que le terme spécifié dans le texte interne est automatiquement ajouté à la liste de mots/dictionnaire/DiscreteExceptions.

- Le terme déconseillé dictionnaire/mots/élément Deprecated/Term ne respecte pas la casse.

- La valeur d’attribut PreferredAlternate respecte la casse. Utiliser la casse Pascal pour les autres termes composés.

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

 Termes dans le nœud de dictionnaire/mots/composés sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : Mots composés doivent être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionnaire/mots/DiscreteExceptions/Term
 Pour exclure un terme dans la liste des termes que l’analyse du code identifie comme une seule, word discret lorsque le terme est vérifié par les règles de casse pour les mots composés, ajoutez ce terme comme texte interne d’un élément de dictionnaire/mots/DiscreteExceptions/Term. Le terme dans l’élément Dictionary/Words/DiscreteExceptions/Term ne respecte pas la casse.

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

 Termes dans le nœud de mots/dictionnaire/DiscreteExceptions sont appliqués aux règles d’analyse du code suivantes :

- [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702 : Mots composés doivent être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionnaire/acronymes/CasingExceptions/acronyme
 Pour inclure un acronyme dans la liste des termes que l’analyse du code identifie comme correctement orthographié et indiquer le fonctionnement des règles de l’acronyme lorsque le terme est vérifié par la casse pour les mots composés, ajoutez ce terme comme texte interne d’un dictionnaire/acronymes/CasingExceptions / Élément Acronym. L’acronyme dans l’élément de dictionnaire/acronymes/CasingExceptions/acronyme respecte la casse.

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

 Termes dans le nœud d’acronymes/dictionnaire/CasingExceptions sont appliqués aux règles d’analyse du code suivantes :

- [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Pour appliquer un dictionnaire personnalisé à un projet

1. Dans **l’Explorateur de solutions**, utilisez une des procédures suivantes :

2. Pour ajouter un dictionnaire à un seul projet, cliquez sur le nom de projet, puis **ajouter un élément existant**. Spécifiez le fichier dans le **ajouter un élément existant** boîte de dialogue.

3. Pour ajouter un dictionnaire qui est partagé entre deux ou plusieurs projets, recherchez le fichier à partager dans le **ajouter un élément existant** boîte de dialogue, cliquez sur la flèche vers le bas sur le **ajouter** bouton, puis cliquez sur **ajouter en tant que lien** .

4. Dans **l’Explorateur de solutions**, cliquez sur le **CustomDictionary.xml** nom de fichier et cliquez sur **propriétés**.

5. À partir de la **Action de génération** liste, sélectionnez **CodeAnalysisDictionary**.

6. À partir de la **Copy to Output Directory** liste, sélectionnez **ne copiez pas**.