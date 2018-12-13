---
title: Définir un espion sur variables | Microsoft Docs
ms.custom: seodec18
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
ms.openlocfilehash: 898c79f3985e24f52620f12dc25ad6044d05ac64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059481"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Regardez des variables avec les fenêtres Espion et Espion express 

Pendant le débogage, vous pouvez utiliser **espion** windows et **Espion express** pour observer les variables et expressions. Les fenêtres sont disponibles uniquement pendant une session de débogage.

**Espion** windows peuvent afficher plusieurs variables à la fois pendant le débogage. Le **Espion express** boîte de dialogue affiche une seule variable à la fois et doit être fermé pour que le débogage puisse se poursuivre.

S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [corriger les bogues en écrivant mieux C# code](../debugger/write-better-code-with-visual-studio.md) et [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

## <a name="observe-variables-with-a-watch-window"></a>Observer variables dans une fenêtre Espion

Vous pouvez ouvrir plusieurs **espion** fenêtre et observer plusieurs variables dans une **espion** fenêtre. 

Par exemple, pour définir un espion sur les valeurs de `a`, `b`, et `c` dans le code suivant :

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

1. Définir un point d’arrêt sur la `c = a + b;` ligne en cliquant dans la marge de gauche, en sélectionnant **déboguer** > **point d’arrêt**, ou en appuyant sur **F9**.
   
1. Démarrer le débogage en sélectionnant le vert **Démarrer** flèche ou **déboguer** > **démarrer le débogage**, ou appuyez sur **F5**. L’exécution s’arrête au point d’arrêt.
   
1. Ouvrir un **espion** en sélectionnant **déboguer** > **Windows** > **espion**  >   **Espion 1**, ou en appuyant sur **Ctrl**+**Alt**+**W** > **1**.
   
   Vous pouvez ouvrir supplémentaires **espion** windows en sélectionnant windows **2**, **3**, ou **4**.
   
1. Dans le **espion** fenêtre, sélectionnez une ligne vide et variable de type `a`. Faites de même pour `b` et `c`.
   
   ![Regardez les variables](../debugger/media/watchvariables.png "WatchVariables")
   
1. Continuer le débogage en sélectionnant **déboguer** > **pas à pas détaillé** ou en appuyant sur **F11** en fonction des besoins pour faire avancer. Les valeurs des variables dans le **espion** fenêtre Modifier pendant que vous parcourez le `for` boucle.
   
>[!NOTE]
>Pour C++ uniquement, 
>- Vous devrez peut-être qualifier le contexte d’un nom de variable ou une expression qui utilise un nom de variable. Le contexte est la fonction, le fichier source ou le module où se trouve une variable. Si vous devez qualifier le contexte, utilisez le [opérateur de contexte (C++)](../debugger/context-operator-cpp.md) syntaxe dans le **nom** dans le **espion** fenêtre. 
>  
>- Vous pouvez ajouter des noms de registres et des noms de variables à l’aide de  **$ \<inscrire&nbsp;nom >** ou  **@ \<inscrire&nbsp;nom >** à la **nom** dans le **espion** fenêtre. Pour plus d’informations, consultez [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Utiliser des expressions dans une fenêtre Espion

Vous pouvez observer toute expression valide reconnue par le débogueur dans un **espion** fenêtre.

Par exemple, pour le code dans la section précédente, vous pouvez obtenir la moyenne des trois valeurs en entrant `(a + b + c) / 3` dans le **espion** fenêtre :

![Expression espionne](../debugger/media/watchexpression.png "expression espionne")

Les règles d’évaluation des expressions dans le **espion** fenêtre sont généralement les mêmes que les règles d’évaluation des expressions dans le langage de code. Si une expression a une erreur de syntaxe, attendez-vous à la même erreur de compilateur, comme dans l’éditeur de code. Par exemple, une faute de frappe dans l’expression précédente génère cette erreur dans le **espion** fenêtre :

![Regardez l’erreur d’expression](../debugger/media/watchexpressionerror.png "regarder l’erreur d’expression")

Un cercle avec une icône de deux lignes ondulées peut-être apparaître dans le **espion** fenêtre. Cette icône signifie que le débogueur n’évalue l’expression en raison d’une dépendance inter-threads potentielle. L’évaluation du code nécessite des autres threads dans votre application pour s’exécuter temporairement, mais étant donné que vous êtes en mode arrêt, tous les threads dans votre application sont généralement arrêtés. Permettre à d’autres threads de s’exécuter temporairement peut avoir des effets inattendus sur l’état de votre application et le débogueur peuvent ignorer certains événements tels que des points d’arrêt et des exceptions sur ces threads.

### <a name="bkmk_refreshWatch"></a> Actualiser les valeurs des espions

Une icône d’actualisation (flèche circulaire) peut apparaître dans le **espion** fenêtre lorsqu’une expression est évaluée. L’icône de rafraîchissement indique une erreur ou une valeur qui est obsolète. 

Pour actualiser la valeur, sélectionnez l’icône d’actualisation, ou appuyez sur la barre d’espace. Le débogueur essaie de réévaluer l'expression. Toutefois, vous ne pouvez pas choix ou être en mesure de réévaluer l’expression, en fonction de la raison pour laquelle la valeur n’a pas été évaluée. 

Placez le curseur sur l’icône d’actualisation ou consultez le **valeur** colonne pour la raison pour laquelle l’expression n’a pas été évaluée. Raisons possibles :

- Une erreur s’est produite car l’expression a été évaluée, comme dans l’exemple précédent. Un délai d’expiration peut se produire, ou une variable peut être hors de portée.
  
- L’expression a un appel de fonction qui peut déclencher un effet secondaire dans l’application. Consultez [Expression effets](#bkmk_sideEffects).
  
- L’évaluation automatique des propriétés et appels de fonction implicite est désactivée. 
  
Si l’icône d’actualisation s’affiche, car l’évaluation automatique des propriétés et appels de fonction implicite est désactivée, vous pouvez l’activer en sélectionnant **activer l’évaluation de la propriété et d’autres appels de fonction implicite** dans **outils**   >  **Options** > **débogage** > **général**.

Pour illustrer l’utilisation de l’icône d’actualisation :

1. Dans **outils** > **Options** > **débogage** > **général**, désactivez le **Activer l’évaluation de la propriété et d’autres appels de fonction implicite** case à cocher. 
   
1. Entrez le code suivant, puis, dans le **espion** fenêtre, définissez un espion sur le `list.Count` propriété. 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. Démarrez le débogage. Le **espion** fenêtre affiche quelque chose comme le message suivant :
   
   ![Actualiser espion](../debugger/media/refreshwatch.png "actualiser espion")
   
1. Pour actualiser la valeur, sélectionnez l’icône d’actualisation, ou appuyez sur la barre d’espace. Le débogueur réévalue l’expression. 

### <a name="bkmk_sideEffects"></a> Expression effets 

Évaluer certaines expressions peut modifier la valeur d’une variable, ou affecter l’état de votre application. Par exemple, l’évaluation de l’expression suivante modifie la valeur de `var1`:

```csharp
var1 = var2
```

Ce code peut entraîner un [effet secondaire](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Effets secondaires peuvent compliquer le débogage en modifiant la façon dont votre application fonctionne.

Une expression avec effets secondaires est évaluée une seule fois, lorsque vous la saisissez. Après cela, l’expression apparaît grisée dans le **espion** fenêtre et davantage d’évaluations sont désactivées. L’info-bulle ou **valeur** colonne explique que l’expression provoque un effet secondaire. Vous pouvez forcer la réévaluation en sélectionnant l’icône d’actualisation qui apparaît en regard de la valeur.

Un moyen d’empêcher la désignation des effets secondaires consiste à désactiver l’évaluation de fonction automatique. Dans **outils** > **Options** > **débogage** > **général**, désélectionnez **Activer l’évaluation de la propriété et d’autres appels de fonction implicite**.

Pour C# uniquement, lors de l’évaluation des propriétés ou des appels de fonction implicite est désactivée, vous pouvez forcer l’évaluation en ajoutant le **ac** modificateur du format à une variable **nom** dans le **espion**  fenêtre. Consultez [Spécificateurs de format en C#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Utiliser l’ID d’objet dans la fenêtre Espion (C# et Visual Basic)

Parfois, vous souhaitez observer le comportement d’un objet spécifique. Par exemple, vous souhaiterez peut-être suivre un objet référencé par une variable locale une fois que cette variable a hors de portée. En C# et Visual Basic, vous pouvez créer des ID d’objet pour des instances spécifiques de types de références et les utiliser dans la fenêtre **Espion** et dans les conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.

> [!NOTE]
> ID d’objet créent des références faibles qui n’empêchent pas l’objet d’une garbage collecté. Leur validité ne vaut que pour la session de débogage active.

Dans le code suivant, le `MakePerson()` méthode crée un `Person` à l’aide d’une variable locale : 

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

Pour connaître le nom de la `Person` dans le `DoSomething()` (méthode), vous pouvez ajouter une référence à la `Person` ID d’objet dans le **espion** fenêtre.

1. Définissez un point d’arrêt dans le code après le `Person` objet a été créé.
   
1. Démarrez le débogage.
   
1. Lors de l’exécution s’arrête au point d’arrêt, ouvrez le **variables locales** fenêtre en choisissant **déboguer** > **Windows** > **devariableslocales**.
   
1. Dans le **variables locales** fenêtre, avec le bouton droit le `Person` variable et sélectionnez **Make Object ID**.
   
   Vous devez voir un signe dollar (**$**) et un nombre dans le **variables locales** fenêtre, qui est l’ID d’objet.
   
1. Ajouter l’ID d’objet pour le **espion** fenêtre en double-cliquant sur l’ID d’objet et en sélectionnant **ajouter un espion**.
   
1. Définir un autre point d’arrêt dans le `DoSomething()` (méthode).
   
1. Poursuivez le débogage. Lorsque l’exécution s’arrête dans le `DoSomething()` (méthode), le **espion** fenêtre affiche le `Person` objet.
   
   > [!NOTE]
   > Si vous souhaitez voir les propriétés de l’objet, tel que `Person.Name`, vous devez activer l’évaluation de la propriété en sélectionnant **outils** > **Options**  >   **Débogage** > **général** > **activer l’évaluation de la propriété et d’autres appels de fonction implicite**.

## <a name="dynamic-view-and-the-watch-window"></a>Affichage dynamique et la fenêtre Espion

Certains langages de script (par exemple, JavaScript ou Python) utilisent dynamique ou [canard](https://en.wikipedia.org/wiki/Duck_typing) tapant et .NET version 4.0 et versions ultérieure prend en charge les objets qui sont difficiles à observer dans les fenêtres de débogage normales.

Le **espion** fenêtre affiche ces objets sous la forme d’objets dynamiques, qui sont créés à partir des types qui implémentent le <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. Nœuds de l’objet dynamique affichent les membres dynamiques des objets dynamiques, mais ne pas autoriser la modification des valeurs de membre. 

Pour actualiser **affichage dynamique** valeurs, sélectionnez le [icône d’actualisation](#bkmk_refreshWatch) en regard du nœud d’objet dynamique. 

Pour afficher uniquement les **affichage dynamique** pour un objet, ajoutez un **dynamique** spécificateur de format après le nom de l’objet dynamique dans le **espion** fenêtre :

- Pour C# : `ObjectName, dynamic`
- Pour Visual Basic : `$dynamic, ObjectName`

>[!NOTE]
>- Le C# débogueur ne réévalue automatiquement les valeurs dans le **affichage dynamique** quand vous passez à la ligne de code suivante. 
>- Le débogueur de Visual Basic actualise automatiquement les expressions ajoutées via la **affichage dynamique**.
>- L’évaluation des membres d’un **affichage dynamique** peut avoir des [effets secondaires](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). 

**Pour insérer un nouvel espion variable qui convertit un objet vers un objet dynamique :**
  
1. Avec le bouton droit n’importe quel enfant d’un **affichage dynamique**.
1. Choisissez **ajouter un espion**. Le `object.name` devient `((dynamic) object).name` et s’affiche dans une nouvelle **espion** fenêtre.

Le débogueur ajoute également un **affichage dynamique** nœud enfant de l’objet à la **automatique** fenêtre. Pour ouvrir le **automatique** fenêtre, pendant le débogage, sélectionnez **déboguer** > **Windows** > **automatique**. 

**Affichage dynamique** améliore également le débogage pour les objets COM. Lorsque le débogueur atteint un objet COM encapsulé dans **System.__ComObject**, il ajoute un **affichage dynamique** nœud pour l’objet.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Observer une seule variable ou une expression avec Espion express

Vous pouvez utiliser **Espion express** pour observer une variable. 

Par exemple, pour le code suivant :

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

Pour observer le `a` variable, 
   
1. Définissez un point d’arrêt sur la ligne `a = a + b;` .
   
1. Démarrez le débogage. L’exécution s’arrête au point d’arrêt.
   
1. Sélectionnez la variable `a` dans le code.
   
1. Sélectionnez **déboguer** > **Espion express**, appuyez sur **MAJ**+**F9**, ou avec le bouton droit et sélectionnez **Espion express**. 
   
   Le **Espion express** boîte de dialogue apparaît. Le `a` variable se trouve dans le **Expression** zone avec un **valeur** de **1**.
   
   ![Variable d’espion Express](../debugger/media/quickwatchvariable.png "variable d’espion Express")
   
1. Pour évaluer une expression à l’aide de la variable, tapez une expression comme `a + b` dans le **Expression** zone, puis sélectionnez **réévaluer**.
   
   ![Expression Espion express](../debugger/media/quickwatchexpression.png "expression Espion express")
   
1. Pour ajouter la variable ou l’expression à partir de **Espion express** à la **espion** fenêtre, sélectionnez **ajouter un espion**.
   
1. Sélectionnez **fermer** pour fermer la **Espion express** fenêtre. (**Espion express** est une boîte de dialogue modale, vous ne pouvez pas poursuivre le débogage tant qu’il est ouvert.)
   
1. Poursuivez le débogage. Vous pouvez observer la variable dans le **espion** fenêtre.

## <a name="see-also"></a>Voir aussi
 [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)  
 [Corriger les bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md)  
 [Premier aperçu de débogage](../debugger/debugger-feature-tour.md) [fenêtres du débogueur](../debugger/debugger-windows.md)
