---
title: Définir un espion sur les Variables dans Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325014"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Définir un espion sur les variables à l’aide des fenêtres Espion et Espion express dans Visual Studio

Pendant le débogage, vous pouvez utiliser la **espion** et **Espion express** pour observer les variables et expressions.  La fenêtre **Espion** permet d’afficher plusieurs variables, à la différence de la fenêtre **Espion express** , qui n’en affiche qu’une à la fois.

Les fenêtres sont disponibles uniquement pendant une session de débogage. Pour ouvrir le **espion** fenêtre, choisissez **déboguer** > **Windows** > **espion**, puis choisissez **Espion 1**, **espion 2**, **espion 3**, ou **espion 4**. Pour ouvrir le **Espion express** fenêtre, soit avec le bouton droit de la variable et choisissez **Espion express**, ou sélectionnez simplement **déboguer** > **Espion express** .

## <a name="observe-variables-with-the-watch-window"></a>Observez les variables dans la fenêtre Espion

Vous pouvez observer plusieurs variables avec la **espion** fenêtre. Par exemple, si vous avez le code suivant :

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

Ajoutez les valeurs des trois variables pour le **espion** fenêtre comme suit :

1. Sélectionnez le `c = a + b;` ligne.

2. Définissez un point d’arrêt (en choisissant **déboguer** > **point d’arrêt** ou en appuyant sur F9).

3. Démarrer le débogage (F5). L'exécution s'arrête au point d'arrêt.

4. Ouvrez le **espion** fenêtre (en choisissant **déboguer** > **Windows** > **espion**  >   **Espion 1**, ou en appuyant sur Ctrl + Alt + W, 1).

5. Sélectionnez une ligne vide et la variable de type `a`. Puis faire la même chose pour les variables `b` et `c`.

   ![Regardez les variables](../debugger/media/watchvariables.png "WatchVariables")

6. Continuer le débogage en appuyant sur F11 que nécessaire pour faire avancer le débogueur.

Vous constatez normalement que les valeurs des variables changent à mesure que vous itérez au sein de la boucle `for` .

Si vous programmez en code natif, vous devrez peut-être parfois qualifier le contexte d’un nom de variable ou une expression qui comporte un nom de variable. Le contexte est la fonction, le fichier source et le module où se trouve une variable. Si vous devez qualifier le contexte, vous pouvez utiliser la syntaxe d’opérateur de contexte. Pour plus d’informations, consultez [opérateur de contexte (C++)](../debugger/context-operator-cpp.md).

## <a name="observe-expressions-with-the-watch-window"></a>Observez les expressions dans la fenêtre Espion

Maintenant nous allons essayer à l’aide d’une expression à la place. Vous pouvez ajouter n’importe quelle expression valide reconnue par le débogueur.

Par exemple, si vous avez le code répertorié dans la section précédente, vous pouvez obtenir la moyenne des trois valeurs à l’aide de cette expression :

![Expression espionne](../debugger/media/watchexpression.png "WatchExpression")

Les règles d’évaluation des expressions dans le **espion** fenêtre sont généralement les mêmes que les règles d’évaluation des expressions dans votre langage de codage. Si votre expression comporte une erreur de syntaxe, attendez-vous à la même erreur du compilateur que vous verriez dans l’éditeur de code. Voici un exemple :

![Regardez l’erreur d’expression](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> Actualiser les valeurs des espions qui sont obsolètes

Une icône d’actualisation (une flèche circulaire) peut apparaître lorsqu’une expression est évaluée dans le **espion** fenêtre. Si vous avez désactivé l’évaluation de la propriété (en choisissant **outils** > **Options** > **débogage**  >   **Général**, puis en désactivant **activer l’évaluation de la propriété et d’autres appels de fonction implicite**), et que vous avez écrit le code suivant :

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

Vous devez voir quelque chose comme l’image suivante si vous définissez un espion sur le `Count` propriété de la liste :

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

L’illustration précédente montre une erreur ou une valeur qui est obsolète. Vous pouvez généralement actualiser la valeur en sélectionnant l’icône, mais dans certains cas vous préférerez peut-être ne pas pour l’actualiser. Vous devez d’abord savoir pourquoi la valeur n’a pas été évaluée.

Une info-bulle fournit des informations sur la raison pour laquelle l’expression n’a pas été évaluée si vous pointez sur l’icône. Si les flèches en cercle s’affichent, l’expression n’a pas été évaluée pour l’une des raisons suivantes :

- Une erreur s’est produite alors que l’expression était en cours d’évaluation. Par exemple, un dépassement de délai a pu se produire ou une variable était peut-être hors de portée.

- L’expression a un appel de fonction susceptible de produire un effet secondaire dans l’application (voir la [effets secondaires et expressions](#bkmk_sideEffects) section).

- Vous avez désactivé l’évaluation automatique des propriétés et appels de fonction implicite par le débogueur (en choisissant **outils** > **Options** > **dedébogage**  >  **Général**, puis en désactivant **activer l’évaluation de la propriété et d’autres appels de fonction implicite**). L’expression ne peut pas être évaluée automatiquement puis.

Pour actualiser la valeur, sélectionnez l’icône d’actualisation, ou appuyez sur la barre d’espace. Le débogueur essaie de réévaluer l'expression. L’icône de rafraîchissement peut-être apparaître, car l’évaluation automatique des propriétés et d’autres appels de fonction implicite a été mises hors tension. Dans ce cas, le débogueur peut évaluer l’expression.

Une icône peut s’afficher un cercle avec deux lignes ondulées ressemblant à des threads. Cette icône signifie que le débogueur n’évalue l’expression en raison d’une dépendance inter-threads potentielle. En d’autres termes, l’évaluation du code nécessite l’exécution temporaire d’autres threads dans votre application. Quand vous êtes en mode arrêt, tous les threads de votre application sont généralement arrêtés. Permettre à d’autres threads de s’exécuter temporairement peut avoir des effets inattendus sur l’état de votre programme et pousse le débogueur à ignorer certains événements tels que les points d’arrêt et les exceptions levées sur ces threads.

## <a name="bkmk_sideEffects"></a> Effets secondaires et expressions

Évaluer certaines expressions peut modifier la valeur d’une variable ou affecter d’une manière ou d’une autre l’état de votre programme. Par exemple, l’évaluation de l’expression suivante modifie la valeur de `var1`:

```csharp
var1 = var2
```

Ce code peut entraîner un [effet secondaire](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Les effets secondaires peuvent rendre le débogage plus difficile en altérant le fonctionnement de votre programme.

Une expression connue pour avoir des effets secondaires est évaluée une seule fois, lorsque vous la saisissez. Autres évaluations sont désactivées. Vous pouvez substituer manuellement ce comportement en sélectionnant l’icône de mise à jour qui s’affiche en regard de la valeur.

La première consiste à éviter tous les effets à désactiver l’évaluation de fonction automatique (en choisissant **outils** > **Options** > **débogage**  >  **Général**, puis en désactivant **activer l’évaluation de la propriété et d’autres appels de fonction implicite**).

Quand l’évaluation des propriétés ou des appels de fonctions implicites est désactivée, vous pouvez forcer l’évaluation en utilisant le modificateur de format **ac** (pour C# uniquement). Consultez [Format specifiers en C#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Utiliser l’ID d’objet dans la fenêtre Espion (c# et Visual Basic)

Il peut arriver que vous souhaitez observer le comportement d’un objet spécifique. Par exemple, vous souhaiterez peut-être suivre un objet référencé par une variable locale une fois que cette variable a hors de portée. En c# et Visual Basic, vous pouvez créer des ID d’objet pour des instances spécifiques des types référence et les utiliser dans le **espion** fenêtre et dans les conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.

> [!NOTE]
> ID d’objet créent des références faibles qui n’empêchent pas l’objet d’une garbage collecté. Leur validité ne vaut que pour la session de débogage active.

Dans le code suivant, une méthode crée un `Person` à l’aide d’une variable locale, mais vous souhaitez en savoir plus ce que le `Person`du nom est dans une autre méthode :

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

Vous pouvez ajouter une référence à cet objet `Person` dans la fenêtre **Espion** comme ceci :

1. Sélectionnez une ligne dans le code qui se produit à que l’objet a été créé.

2. Définissez un point d’arrêt (en choisissant **déboguer** > **point d’arrêt** ou en appuyant sur F9).

3. Démarrez le débogage.

4. Lors de l’exécution s’arrête au point d’arrêt, ouvrez le **variables locales** fenêtre (en choisissant **déboguer** > **Windows** > **devariableslocales**), avec le bouton droit de la variable, puis sélectionnez **Make Object ID**.

   Vous devez voir un signe dollar (**$**) et un nombre dans le **variables locales** fenêtre, qui est l’ID d’objet.

   > [!NOTE]
   > Si vous souhaitez voir les propriétés de l’objet, tel que `Person.Name`, vous devez activer l’évaluation de la propriété en choisissant **outils** > **Options**  >   **Débogage** > **général**, puis en définissant **activer l’évaluation de la propriété et d’autres appels de fonction implicite**.

5. Ajouter l’ID d’objet pour le **espion** fenêtre en double-cliquant sur le signe dollar et le numéro, puis en choisissant **ajouter un espion**.

6. Définissez un point d’arrêt dans lequel vous voulez observer le comportement de l’objet.  Dans le code précédent, qui serait le `DoSomething()` (méthode).

7. Poursuivez le débogage. Lorsque l’exécution s’interrompt le `DoSomething()` (méthode), le **espion** fenêtre affiche le `Person` objet.

## <a name="use-registers-in-the-watch-window-c-only"></a>Utiliser des registres dans la fenêtre Espion (C++ uniquement)

Vous pouvez ajouter des noms de registres et des noms de variables à l’aide de  **$ \<inscrire&nbsp;nom >** ou  **@ \<inscrire&nbsp;nom >** pendant le débogage de code natif. Pour plus d’informations, consultez [Pseudovariables](../debugger/pseudovariables.md).

## <a name="dynamic-view-and-the-watch-window"></a>Affichage dynamique et la fenêtre Espion

Certains langages de script (par exemple, JavaScript ou Python) utilisent dynamique ou [canard tapant](https://en.wikipedia.org/wiki/Duck_typing), et les langages .NET (version 4.0 et versions ultérieur) prennent en charge les objets qui sont difficiles à observer dans les fenêtres de débogage normales, car ils peut avoir des propriétés d’exécution et des méthodes qui ne peut pas être affichées.

Le **espion** fenêtre peut afficher un objet dynamique, qui est créé à partir d’un type qui implémente le <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Lorsque cet objet est affiché, le débogueur ajoute un spécial **affichage dynamique** nœud enfant de l’objet si vous ouvrez le **automatique** fenêtre (en choisissant **déboguer**  >  **Windows** > **automatique**). Ce nœud affiche les membres dynamiques de l’objet dynamique, mais n’autorise la modification des valeurs de membre.

Pour insérer un nouvel espion variable qui convertit un objet vers un objet dynamique :

1. Avec le bouton droit n’importe quel enfant d’un **affichage dynamique**.
2. Choisissez **ajouter un espion**. Puis `object.name` devient `((dynamic) object).name`.

L’évaluation des membres d’un **Affichage dynamique** peut avoir des effets secondaires. Pour obtenir une explication de ces effets secondaires, consultez le [effets secondaires et expressions](#bkmk_sideEffects) section. Pour c#, le débogueur ne réévalue automatiquement les valeurs indiquées dans le **affichage dynamique** quand vous passez à une nouvelle ligne de code. Pour Visual Basic, les expressions ajoutées via l’ **Affichage dynamique** sont automatiquement actualisées.

Pour obtenir des instructions sur la façon d’actualiser le **affichage dynamique** valeurs, consultez le [valeurs espion actualiser qui sont devenus obsolètes pour](#bkmk_refreshWatch) section.

Si vous souhaitez afficher uniquement les **affichage dynamique** pour un objet, vous pouvez utiliser la **dynamique** format spécificateur dans le **espion** fenêtre :

- C#: `ObjectName, dynamic`
- Visual Basic : `$dynamic, ObjectName`

Par ailleurs, l’ **Affichage dynamique** améliore l’expérience de débogage pour les objets COM. Lorsque le débogueur atteint un objet COM encapsulé dans **System.__ComObject**, il ajoute un **affichage dynamique** nœud pour l’objet.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observer une seule variable ou une expression avec Espion express

Vous pouvez utiliser la fenêtre **Espion express** pour observer une variable déterminée. Par exemple, si vous avez le code suivant :

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

Vous pouvez observer une variable dans le **Espion express** fenêtre comme suit :

1. Définissez un point d’arrêt sur la ligne `a = a + b;` .

2. Démarrez le débogage. L'exécution s'arrête au point d'arrêt.

3. Sélectionnez la variable `a`.

4. Choisissez **déboguer** > **Espion express** ou appuyez sur **MAJ + F9**. Le **Espion express** fenêtre s’affiche. Dans le **valeur** zone, le `a` variable s’affiche avec la valeur 1.

   ![Variable d’espion Express](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   Pour évaluer une expression à l’aide de la variable, tapez une expression comme `a + b` à la **Expression** , puis cliquez sur **réévaluer**.

   ![Expression Espion express](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   Pour ajouter la variable ou l’expression à la **espion** fenêtre à partir de **Espion express**, choisissez **ajouter un espion**.

   > [!NOTE]
   > Le **Espion express** fenêtre est une fenêtre de la boîte de dialogue modale, vous ne pouvez pas poursuivre le débogage tant qu’il est ouvert.

5. Fermez la fenêtre **Espion express** . Dès lors, vous pouvez poursuivre le débogage pendant que vous observez la valeur dans la fenêtre **Espion** .

## <a name="see-also"></a>Voir aussi

[Fenêtres du débogueur](../debugger/debugger-windows.md)
