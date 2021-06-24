---
title: Afficher des informations personnalisées à l’aide de DebuggerDisplay | Microsoft Docs
description: Utilisez une instance de DebuggerDisplayAttribute pour contrôler l’affichage d’un objet, d’une propriété ou d’un champ dans les fenêtres de variables du débogueur.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: how-to
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e9579e4969cb53ed2f1bcf749e8114386af85d0
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602144"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Indiquez au débogueur ce qui doit être affiché à l’aide de l’attribut DebuggerDisplay (C#, Visual Basic, F #, C++/CLI)

La <xref:System.Diagnostics.DebuggerDisplayAttribute> contrôle la façon dont un objet, une propriété ou un champ s’affiche dans les fenêtres de variables du débogueur. Cet attribut peut être appliqué aux éléments suivants : types, délégués, propriétés, champs et assemblys. En cas d’application à un type de base, l’attribut s’applique également à une sous-classe.

L'attribut `DebuggerDisplay` possède un seul argument, qui est une chaîne à afficher dans la colonne valeur des instances du type. Cette chaîne peut contenir des accolades (`{` et `}`). Le texte entre deux accolades est évalué comme un champ, une propriété ou une méthode.

Si une classe possède une méthode `ToString()` substituée, le débogueur utilise la méthode substituée à la place du `{<typeName>}`par défaut. Si vous avez substitué la méthode `ToString()` , le débogueur utilise la méthode substituée à la place du`{<typeName>}`par défaut. Il est donc inutile d’utiliser `DebuggerDisplay`. Si vous utilisez les deux, l’attribut `DebuggerDisplay` est prioritaire sur la méthode `ToString()` remplacée. L' `DebuggerDisplay` attribut a également priorité sur la méthode substituée `ToString()` dans une sous-classe.

Le fait que le débogueur évalue cet appel implicite `ToString()` dépend d’un paramètre utilisateur dans la boîte de dialogue **Outils/Options/débogage** .

> [!IMPORTANT]
> Si la case à cocher **afficher la structure brute des objets dans les fenêtres de variables** est activée dans la boîte de dialogue **Outils/Options/débogage** , l' `DebuggerDisplay` attribut est ignoré.

> [!NOTE]
> Pour le code natif, cet attribut est pris en charge uniquement dans le code C++/CLI.

Le tableau suivant montre quelques-unes des utilisations possibles de l'attribut `DebuggerDisplay` et quelques exemples de sorties.

|Attribut|Sortie apparaissant dans la colonne Valeur|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Utilisé sur un type avec champs `x` et `y`.|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`La syntaxe des paramètres peut varier d'un langage à l'autre. Par conséquent, soyez vigilant dans son emploi.|`String value is [5, 6, 6]`|

`DebuggerDisplay` peut également accepter des paramètres nommés.

|Paramètres|Objectif|
|----------------|-------------|
|`Name`, `Type`|Ces paramètres affectent les colonnes **Nom** et **Type** des fenêtres de variables. (Ils peuvent être appliqués aux chaînes à l'aide de la même syntaxe que le constructeur). Une utilisation excessive ou inappropriée de ces paramètres peut générer un résultat confus.|
|`Target`, `TargetTypeName`|Spécifie le type cible lorsque l'attribut est utilisé au niveau de l'assembly.|

Le fichier autoexp.cs utilise l’attribut DebuggerDisplay au niveau de l’assembly. Le fichier autoexp.cs détermine les expansions par défaut utilisées par Visual Studio pour les objets .NET. Vous pouvez examiner le fichier autoexp.cs pour obtenir des exemples d’utilisation de l’attribut DebuggerDisplay, ou modifier et compiler le fichier autoexp.cs pour changer les expansions par défaut. Assurez-vous d'avoir sauvegardé le fichier autoexp.cs avant de le modifier.

Pour générer autoexp.cs, ouvrez une Invite de commandes développeur pour VS2015, puis exécutez les commandes suivantes :

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Les modifications apportées à autoexp.dll seront récupérées lors de la prochaine session de débogage.

## <a name="using-expressions-in-debuggerdisplay"></a>Utilisation d'expressions dans DebuggerDisplay
Bien que vous puissiez utiliser une expression générale à l'intérieur de l'accolade dans un attribut DebuggerDisplay, cette méthode n'est pas recommandée.

Une expression générale DebuggerDisplay dispose d'un accès implicite au pointeur `this` pour l'instance actuelle du type de cible uniquement. L'expression n'a accès ni aux alias, ni aux variables locales, ni aux pointeurs. Si l'expression référence des propriétés, les attributs de ces propriétés ne sont pas traités. Par exemple, le code C# `[DebuggerDisplay("Object {count - 2}")]` afficherait `Object 6` si le champ `count` avait la valeur 8.

L'utilisation d'expressions dans DebuggerDisplay peut provoquer les problèmes suivants :

- L'évaluation des expressions est l'opération la plus coûteuse dans le débogueur et l'expression est évaluée chaque fois qu'elle est affichée. Cela peut provoquer des problèmes de performances pendant l'exécution du code pas à pas. Par exemple, une expression complexe qui est utilisée pour afficher des valeurs dans une collection ou une liste peut être très lente lorsque le nombre d'éléments est important.

- Les expressions sont évaluées par l'évaluateur d'expression du langage du cadre de pile actuel et pas par l'évaluateur du langage dans lequel l'expression a été écrite. Cela peut provoquer des résultats inattendus lorsque les langages sont différents.

- L'évaluation d'une expression peut modifier l'état de l'application. Par exemple, une expression qui définit la valeur d'une propriété transforme la valeur d'une propriété dans le code en cours de exécution.

  Une façon de réduire les problèmes potentiels de l'évaluation de l'expression consiste à créer une propriété privée qui exécute l'opération et retourne une chaîne. L'attribut DebuggerDisplay peut ensuite afficher la valeur de cette propriété privée. L'exemple suivant implémente ce modèle :

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

Le suffixe « , NQ » indique à l’évaluateur d’expression de supprimer les guillemets lors de l’affichage de la valeur finale (NQ = no Quotations).

## <a name="example"></a>Exemple
L'exemple de code suivant explique l'utilisation de `DebuggerDisplay`, ainsi que de `DebuggerBrowsable` et `DebuggerTypeProxy`. Lorsqu'il s'affiche dans une fenêtre de variables du débogueur, comme la fenêtre **Espion** , il produit une expansion de ce genre :

|**Nom**|**Valeur**|**Type**|
|--------------|---------------|--------------|
|Clé :|"trois"|objet {string}|
|Valeur|3|objet {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de l'attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-managed-objects.md)
- [Spécificateurs de format en C#](../debugger/format-specifiers-in-csharp.md)
- [Amélioration du débogage avec les attributs d'affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
