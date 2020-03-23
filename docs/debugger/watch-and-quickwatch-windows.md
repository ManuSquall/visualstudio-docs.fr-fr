---
title: Réglez une montre sur les variables . Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302006"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Regarder les variables avec les fenêtres Watch et QuickWatch

Pendant que vous débugging, vous pouvez utiliser **watch** windows et **QuickWatch** pour regarder les variables et les expressions. Les fenêtres ne sont disponibles que lors d’une séance de débogage.

**Les** fenêtres de montre peuvent afficher plusieurs variables à la fois tout en débogage. Le dialogue **QuickWatch** affiche une seule variable à la fois, et doit être fermé avant que le débogage puisse continuer.

Si c’est la première fois que vous avez essayé de déboguer du code, vous pouvez lire [Debugging pour les débutants absolus](../debugger/debugging-absolute-beginners.md) et [les techniques et les outils Debugging](../debugger/write-better-code-with-visual-studio.md) avant de passer par cet article.

## <a name="observe-variables-with-a-watch-window"></a>Observer les variables avec une fenêtre de montre

Vous pouvez ouvrir plus d’une fenêtre **de montre,** et observer plus d’une variable dans une fenêtre **de montre.**

Par exemple, pour définir une `a`montre `b`sur `c` les valeurs de , , et dans le code suivant:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Définissez un point `c = a + b;` d’arrêt sur la ligne en cliquant sur la marge gauche, en sélectionnant **Debug** > **Toggle Breakpoint**, ou en appuyant sur **F9**.

1. Commencez à débogage en sélectionnant la flèche **de démarrage** verte ou **Debug** > **Start Debugging**, ou appuyez sur **F5**. L’exécution s’arrête au point d’arrêt.

1. Ouvrez une fenêtre **Watch** en sélectionnant **Debug** > **Windows** > **Watch** > **Watch 1**, ou en appuyant sur **Ctrl**+**Alt**+**W** > **1**.

   Vous pouvez ouvrir des fenêtres **de montre** supplémentaires en sélectionnant les fenêtres **2**, **3**, ou **4**.

1. Dans la fenêtre **Watch,** sélectionnez une `a`rangée vide, et tapez variable . Faites la `b` même `c`chose pour et .

   ![Regarder les variables](../debugger/media/watchvariables.png "RegarderVariables")

1. Continuer à débogage en sélectionnant **Debug** > **Step Into** ou en appuyant sur **F11** au besoin pour avancer. Les valeurs variables de la fenêtre **Watch** changent `for` au fur et à mesure que vous itérerez à travers la boucle.

>[!NOTE]
>Pour le Cmd seulement,
>- Vous devrez peut-être qualifier le contexte d’un nom variable ou d’une expression qui utilise un nom variable. Le contexte est la fonction, le fichier source ou le module où se trouve une variable. Si vous devez qualifier le contexte, utilisez la syntaxe [contextuelle (C)](../debugger/context-operator-cpp.md) dans la fenêtre **Name** in the **Watch.**
>
>- Vous pouvez ajouter des noms de registre et des noms variables à l’aide ** $ \<du nom&nbsp;du registre>** ou ** @ \<enregistrer&nbsp;** le nom>à la fenêtre **Nom** dans la **montre.** Pour plus d’informations, consultez [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Utiliser des expressions dans une fenêtre de montre

Vous pouvez observer toute expression valide reconnue par le débbuggeur dans une fenêtre **de montre.**

Par exemple, pour le code de la section précédente, vous `(a + b + c) / 3` pouvez obtenir la moyenne des trois valeurs en entrant dans la fenêtre **Watch** :

![Regarder l’expression](../debugger/media/watchexpression.png "Regarder l’expression")

Les règles d’évaluation des expressions dans la fenêtre **Watch** sont généralement les mêmes que les règles d’évaluation des expressions dans le langage du code. Si une expression a une erreur de syntaxe, attendez-vous à la même erreur de compilateur que dans l’éditeur de code. Par exemple, une faute de frappe dans l’expression précédente produit cette erreur dans la fenêtre **Watch** :

![Regarder l’erreur d’expression](../debugger/media/watchexpressionerror.png "Regarder l’erreur d’expression")

Un cercle avec deux lignes ondulées icône peut apparaître dans la fenêtre **de la montre.** Cette icône signifie que le débbuggeur n’évalue pas l’expression en raison d’une dépendance potentielle de fil croisé. L’évaluation du code nécessite que d’autres threads de votre application s’exécutent temporairement, mais puisque vous êtes en mode pause, tous les threads de votre application sont généralement arrêtés. Permettre à d’autres threads de s’exécuter temporairement peut avoir des effets inattendus sur l’état de votre application, et le débbuggeur peut ignorer des événements tels que les points d’arrêt et les exceptions sur ces fils.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Rechercher dans la fenêtre Watch

Vous pouvez rechercher des mots clés dans les colonnes nom, valeur et type de la fenêtre **Watch** à l’aide de la barre de recherche au-dessus de chaque fenêtre. Frappez ENTER ou sélectionnez l’une des flèches pour exécuter une recherche. Pour annuler une recherche en cours, sélectionnez l’icône "x" dans la barre de recherche.

Utilisez les flèches gauche et droite (Shift-F3 et F3, respectivement) pour naviguer entre les allumettes trouvées.

![Rechercher dans Watch Window](../debugger/media/ee-search-watch.png "Rechercher dans Watch Window")

Pour rendre votre recherche plus ou moins approfondie, utilisez le dropdown **Search Deeper** en haut de la fenêtre **Watch** pour sélectionner le nombre de niveaux de profondeur que vous souhaitez rechercher dans des objets imbriqués. 

## <a name="pin-properties-in-the-watch-window"></a>Propriétés d’épingle dans la fenêtre de montre

>[!NOTE]
> Cette fonctionnalité est prise en charge dans .NET Core 3.0 ou plus.

Vous pouvez inspecter rapidement les objets par leurs propriétés dans la fenêtre Watch avec **l’outil Pinnable Properties.**  Pour utiliser cet outil, survolez une propriété et sélectionnez l’icône de broche qui apparaît ou en clic droit et sélectionnez le **membre Pin comme** option préférée dans le menu contextuelle résultant.  Cela bouillonne jusqu’à cette propriété en haut de la liste des propriétés de l’objet, et le nom et la valeur de la propriété est affiché dans la colonne **de** valeur.  Pour défoncé une propriété, sélectionnez à nouveau l’icône de la broche ou sélectionnez le **membre Unpin comme** option préférée dans le menu contextuelle.

![Propriétés d’épingle dans la fenêtre de montre](../debugger/media/basic-pin-watch.gif "Propriétés d’épingle dans la fenêtre de montre")

Vous pouvez également basculer les noms de propriété et filtrer les propriétés non épinglées lors de l’affichage de la liste des propriétés de l’objet dans la fenêtre De la montre.  Vous pouvez accéder aux deux options en sélectionnant les boutons dans la barre d’outils au-dessus de la fenêtre de la montre.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Rafraîchir les valeurs de la montre

Une icône de rafraîchissement (flèche circulaire) peut apparaître dans la fenêtre de la **montre** lorsqu’une expression est évaluée. L’icône de rafraîchissement indique une erreur ou une valeur périmée.

Pour actualiser la valeur, sélectionnez l’icône de rafraîchissement ou appuyez sur la barre d’espace. Le débogueur essaie de réévaluer l'expression. Cependant, vous ne pouvez pas vouloir ou être en mesure de réévaluer l’expression, selon pourquoi la valeur n’a pas été évaluée.

Planer au-dessus de l’icône de rafraîchissement ou voir la colonne **de valeur** pour la raison que l’expression n’a pas été évaluée. En voici plusieurs raisons :

- Une erreur s’est produite au fur et à mesure que l’expression était évaluée, comme dans l’exemple précédent. Un délai d’attente peut se produire, ou une variable peut être hors de portée.

- L’expression a un appel de fonction qui pourrait déclencher un effet secondaire dans l’application. Voir [Effets secondaires Expression](#bkmk_sideEffects).

- L’évaluation automatique des propriétés et des appels de fonction implicites est désactivée.

Si l’icône de rafraîchissement apparaît parce que l’évaluation automatique des propriétés et des appels de fonction implicite est désactivée, vous pouvez l’activer en sélectionnant **l’évaluation de propriété d’activation et d’autres appels implicites** de fonction dans les options > **d’outils** > **Debugging** > **général.** **Tools**

Pour démontrer à l’aide de l’icône de rafraîchissement :

1. Dans **Tools** > **Options** > **Debugging** > **General**, effacer l’évaluation de propriété Enable et **d’autres appels de fonction implicites coche.**

1. Entrez le code suivant, et dans la `list.Count` fenêtre de la **montre,** définissez une montre sur la propriété.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Démarrez le débogage. La fenêtre **Watch** montre quelque chose comme le message suivant:

   ![Montre De rafraîchissement](../debugger/media/refreshwatch.png "Montre De rafraîchissement")

1. Pour actualiser la valeur, sélectionnez l’icône de rafraîchissement ou appuyez sur la barre d’espace. Le débbuggeur réévalue l’expression.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Effets secondaires d’expression

L’évaluation de certaines expressions peut modifier la valeur d’une variable, ou autrement affecter l’état de votre application. Par exemple, l’évaluation de l’expression suivante modifie la valeur de `var1`:

```csharp
var1 = var2
```

Ce code peut provoquer un [effet secondaire](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Les effets secondaires peuvent rendre le débogage plus difficile en modifiant le fonctionnement de votre application.

Une expression avec des effets secondaires n’est évaluée qu’une seule fois, lorsque vous y entrez pour la première fois. Après cela, l’expression semble grisée dans la fenêtre de la **montre,** et d’autres évaluations sont désactivées. La colonne de pointe ou **de valeur** explique que l’expression provoque un effet secondaire. Vous pouvez forcer la réévaluation en sélectionnant l’icône de rafraîchissement qui apparaît à côté de la valeur.

Une façon d’empêcher la désignation d’effets secondaires est d’éteindre l’évaluation automatique de la fonction. Dans **Tools** > **Options** > **Debugging** > **General**, désélection Enable évaluation de la propriété et autres appels de fonction **implicite**.

Pour C seulement, lorsque l’évaluation des propriétés ou des appels de fonction implicite est désactivé, vous pouvez forcer l’évaluation en ajoutant le modificateur de format **ac** à un **nom** variable dans la fenêtre **de montre.** Voir [les spécificateurs de format en C .](../debugger/format-specifiers-in-csharp.md)

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Utilisez des DIU d’objets dans la fenêtre Watch (C et Visual Basic)

Parfois, vous voulez observer le comportement d’un objet spécifique. Par exemple, vous pouvez suivre un objet mentionné par une variable locale après que cette variable a disparu de portée. Dans le C et Visual Basic, vous pouvez créer des cartes d’identité d’objet pour des cas spécifiques de types de référence, et les utiliser dans la fenêtre **Watch** et dans des conditions de point de rupture. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.

> [!NOTE]
> Les pièces d’ID d’objet créent des références faibles qui n’empêchent pas l’objet d’être ramassé. Leur validité ne vaut que pour la session de débogage active.

Dans le code `MakePerson()` suivant, `Person` la méthode crée une variable locale :

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Pour connaître le nom `Person` de `DoSomething()` la méthode, vous pouvez `Person` ajouter une référence à l’IDENTIFIANT d’objet dans la fenêtre **Watch.**

1. Définissez un point d’arrêt dans le code après la création de l’objet. `Person`

1. Démarrez le débogage.

1. Lorsque l’exécution s’arrête au point d’arrêt, ouvrez la fenêtre **des sections locales** en choisissant **Debug** > **Windows** > **Locals**.

1. Dans la fenêtre **Locals,** `Person` cliquez à droite sur la variable et sélectionnez **Make Object ID**.

   Vous devriez voir un**$** signe d’un dollar ( ) plus un numéro dans la fenêtre **local,** qui est l’id d’objet.

1. Ajoutez l’ID d’objet à la fenêtre **De la montre** en cliquant à droite sur l’identifiant d’objet et en sélectionnant Add **Watch**.

1. Définissez un autre `DoSomething()` point d’arrêt dans la méthode.

1. Poursuivez le débogage. Lorsque l’exécution `DoSomething()` s’arrête dans la `Person` méthode, la fenêtre **Watch** affiche l’objet.

   > [!NOTE]
   > Si vous voulez voir les propriétés `Person.Name`de l’objet, telles que , vous devez activer l’évaluation de la propriété en sélectionnant des options > **d’outils** > **Debugging** > **General** > **Enable évaluation de la propriété et d’autres appels de fonction implicite**. **Tools**

## <a name="dynamic-view-and-the-watch-window"></a>Vue dynamique et la fenêtre de montre

Certaines langues de script (par exemple, JavaScript ou Python) utilisent la saisie dynamique ou [de canard,](https://en.wikipedia.org/wiki/Duck_typing) et la version .NET 4.0 et prend en charge plus tard les objets qui sont difficiles à observer dans les fenêtres de débogage normales.

La fenêtre **Watch** affiche ces objets comme des objets <xref:System.Dynamic.IDynamicMetaObjectProvider> dynamiques, qui sont créés à partir de types qui implémentent l’interface. Les nœuds d’objets dynamiques montrent les membres dynamiques des objets dynamiques, mais n’autorisent pas l’édition des valeurs du membre.

Pour actualiser les valeurs **Dynamic View,** sélectionnez l’icône [de rafraîchissement](#bkmk_refreshWatch) à côté du nœud d’objet dynamique.

Pour afficher uniquement la **vue dynamique** pour un objet, ajoutez un spécificateur de format **dynamique** d’après le nom dynamique de l’objet dans la fenêtre **Watch** :

- Pour C# : `ObjectName, dynamic`
- Pour Visual Basic : `$dynamic, ObjectName`

>[!NOTE]
>- Le débingière C N’est pas automatiquement réévaluer les valeurs de la **vision dynamique** lorsque vous entrez dans la ligne de code suivante.
>- Le débbuggeur Visual Basic actualise automatiquement les expressions ajoutées par la **vue dynamique**.
>- L’évaluation des membres d’une **vue dynamique** peut avoir des [effets secondaires](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Pour insérer une nouvelle variable de montre qui jette un objet vers un objet dynamique :**

1. Cliquez à droite sur n’importe quel enfant d’une **vue dynamique**.
1. Choisissez **Add Watch**. Le `object.name` `((dynamic) object).name` devient et apparaît dans une nouvelle fenêtre **de montre.**

Le débogénaire ajoute également un nœud d’enfant **Dynamic View** de l’objet à la fenêtre **Autos.** Pour ouvrir la fenêtre **Autos,** lors du débogage, sélectionnez **Debug** > **Windows** > **Autos**.

**Dynamic View** améliore également le débogage pour les objets COM. Lorsque le débbuggeur arrive à un objet COM enveloppé dans **System.__ComObject**, il ajoute un nœud **Vision dynamique** pour l’objet.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observez une seule variable ou expression avec QuickWatch

Vous pouvez utiliser **QuickWatch** pour observer une seule variable.

Par exemple, pour le code suivant :

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Pour observer `a` la variable,

1. Définissez un point d’arrêt sur la ligne `a = a + b;` .

1. Démarrez le débogage. L’exécution s’arrête au point d’arrêt.

1. Sélectionnez `a` la variable dans le code.

1. Sélectionnez **Debug** > **QuickWatch**, appuyez sur **Shift**+**F9**, ou cliquez à droite et sélectionnez **QuickWatch**.

   Le dialogue **QuickWatch** apparaît. La `a` variable est dans la boîte **d’expression** avec une **valeur** de **1**.

   ![Variable QuickWatch](../debugger/media/quickwatchvariable.png "Variable QuickWatch")

1. Pour évaluer une expression à l’aide `a + b` de la variable, tapez une expression comme dans la boîte **Expression,** et **sélectionnez Reevaluate**.

   ![Expression QuickWatch](../debugger/media/quickwatchexpression.png "Expression QuickWatch")

1. Pour ajouter la variable ou l’expression de **QuickWatch** à la fenêtre **Watch,** sélectionnez **Add Watch**.

1. Sélectionnez **Près** pour fermer la fenêtre **QuickWatch.** (**QuickWatch** est un dialogue modal, de sorte que vous ne pouvez pas continuer à débogage tant qu’il est ouvert.)

1. Poursuivez le débogage. Vous pouvez observer la variable dans la fenêtre **Watch.**

## <a name="see-also"></a>Voir aussi
- [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)
- [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md)
- [Premier regard sur le débogage](../debugger/debugger-feature-tour.md)
- [Fenêtres Debugger](../debugger/debugger-windows.md)
