---
title: Espion et Espion express Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fa22e93a767df599815c87e5809faddb674854b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953394"
---
# <a name="watch-and-quickwatch-windows"></a>Espion et Espion express, fenêtres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser la **espion** (**déboguer / Windows / espion / espion (1, 2, 3, 4)**) et **Espion express** (avec le bouton droit sur la variable / **déboguer / Espion express**) pour observer les variables et expressions pendant une session de débogage.  La fenêtre **Espion** permet d’afficher plusieurs variables, à la différence de la fenêtre **Espion express** , qui n’en affiche qu’une à la fois.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Observation d’une variable dans la fenêtre Espion express  
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
  
 Vous pouvez observer la variable a dans la fenêtre Espion express de la façon suivante :  
  
1.  Définissez un point d’arrêt sur la ligne `a = a + b;` .  
  
2.  Démarrez le débogage. L’exécution s’interrompt au point d’arrêt.  
  
3.  Ouvrez la fenêtre **Espion express** (cliquez avec le bouton droit sur a, puis choisissez **Déboguer/Espion express**ou **Maj+F9**). Vous pouvez ouvrir la fenêtre et ajouter la variable a à la fenêtre **Expression** , puis cliquer sur **Réévaluer**. La variable a s’affiche alors dans la fenêtre **Valeurs** avec une valeur égale à 2.  
  
4.  La fenêtre **Espion express** étant une boîte de dialogue modale, vous ne pouvez pas poursuivre le débogage tant qu’elle est ouverte. Vous pouvez ajouter la variable à la fenêtre **Espion** en cliquant sur **Ajouter un espion**.  
  
5.  Fermez la fenêtre **Espion express** . Dès lors, vous pouvez poursuivre le débogage pendant que vous observez la valeur dans la fenêtre **Espion** .  
  
## <a name="observing-variables-with-the-watch-window"></a>Observation de variables dans la fenêtre Espion  
 Vous pouvez observer plusieurs variables dans la fenêtre **Espion** . Par exemple, si vous avez le code suivant :  
  
```csharp  
static void Main(string[] args)  
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
}  
  
```  
  
 Ajoutez les valeurs des trois variables à la fenêtre Espion de la façon suivante :  
  
1. Définissez un point d’arrêt sur la ligne `c = a + b;` .  
  
2. Démarrez le débogage (**F5**) L'exécution s'arrête au point d'arrêt.  
  
3. Ouvrez la fenêtre Espion (**Déboguer/Fenêtres/Espion/Espion 1**ou **Ctrl+Alt+W, 1**).  
  
4. Ajoutez la variable `a` à la première ligne, la variable `b` à la deuxième ligne et la variable `c` à la troisième ligne.  
  
5. Poursuivez le débogage.  
  
   Vous constatez normalement que les valeurs des variables changent à mesure que vous itérez au sein de la boucle `for` .  
  
   Si vous programmez en code natif, vous devrez peut-être parfois qualifier le contexte d’un nom de variable ou d’une expression contenant un nom de variable. Le contexte est la fonction, le fichier source et le module où se trouve une variable. Dans ce cas, vous pouvez utiliser la syntaxe d’opérateur de contexte. Pour plus d’informations, consultez Expressions en C++.  
  
## <a name="observing-expressions-with-the-watch-window"></a>Observation d’expressions dans la fenêtre Espion  
 Maintenant, essayons d’utiliser une expression. Vous pouvez ajouter n’importe quelle expression valide reconnue par le débogueur.  
  
 Par exemple, si vous avez le code présenté dans la section précédente, vous pouvez obtenir la moyenne des trois valeurs comme ceci :  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 En général, les règles d’évaluation des expressions dans la fenêtre **Espion** sont les mêmes que dans votre langage de codage. Si votre expression contient une erreur de syntaxe, vous pouvez vous attendre à voir la même erreur de compilateur dans l’éditeur de code. Voici un exemple :  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Actualisation des valeurs obsolètes dans la fenêtre Espion  
 Dans certaines circonstances, une icône d’actualisation (cercle avec deux flèches ou cercle avec deux lignes ondulées) peut apparaître pendant l’évaluation d’une expression dans la fenêtre **Espion** .  Par exemple, si vous avez désactivé l’évaluation de propriété (**Outils/Options/Débogage/Activer l’évaluation de la propriété et d’autres appels de fonction implicite**) et que vous avez le code suivant :  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Si vous définissez un espion dans la propriété `Count` de la liste, voici ce que vous devriez voir :  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Cela indique la présence d’une erreur ou d’une valeur obsolète. Vous pouvez généralement actualiser la valeur en cliquant sur l’icône, mais dans certains cas, vous préférerez ne pas l’actualiser. Vous devez d’abord savoir pourquoi la valeur n’a pas été évaluée.  
  
 Si vous pointez sur l’icône, une info-bulle vous donne des indications sur ce qui a empêché l’évaluation de l’expression.  Si les flèches en cercle s’affichent, c’est que l’expression n’a pas été évaluée pour l’une des raisons suivantes :  
  
- • Une erreur s’est produite car l’expression a été évaluée. Par exemple, un dépassement de délai a pu se produire ou une variable était peut-être hors de portée.  
  
- • L’expression contient un appel de fonction susceptible de produire un effet secondaire dans l’application (consultez [effets secondaires et Expressions](#bkmk_sideEffects)).  
  
- L’évaluation automatique des propriétés et des appels de fonctions implicites par le débogueur est désactivée (**Outils/Options/Débogage/Activer l’évaluation de la propriété et d’autres appels de fonction implicite**), d’où l’impossibilité d’évaluer automatiquement l’expression.  
  
  Pour actualiser la valeur, cliquez sur l’icône d’actualisation ou appuyez sur la barre d’espace. Le débogueur essaie de réévaluer l’expression. Si l’icône d’actualisation est apparue parce que l’évaluation automatique des propriétés et les effets secondaires implicites étaient désactivés, l’expression peut être évaluée.  
  
  Si vous voyez une icône représentant un cercle avec deux lignes ondulées qui s’apparentent à des fils, c’est que l’expression n’a pas été évaluée en raison d’une possible dépendance inter-threads. En d’autres termes, l’évaluation du code nécessite l’exécution temporaire d’autres threads dans votre application. Quand vous êtes en mode arrêt, tous les threads de votre application sont généralement arrêtés. Permettre à d’autres threads de s’exécuter temporairement peut avoir des effets inattendus sur l’état de votre programme et pousse le débogueur à ignorer certains événements tels que les points d’arrêt et les exceptions levées sur ces threads.  
  
##  <a name="bkmk_sideEffects"></a> Side Effects and Expressions  
 Évaluer certaines expressions peut modifier la valeur d’une variable ou affecter d’une manière ou d’une autre l’état de votre programme. Par exemple, l’évaluation de l’expression suivante modifie la valeur de `var1`:  
  
```  
var1 = var2  
```  
  
 C’est ce que l’on appelle un [effet secondaire](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Les effets secondaires peuvent rendre le débogage plus difficile en altérant le fonctionnement de votre programme.  
  
 Une expression connue pour avoir des effets secondaires n’est évaluée qu’une seule fois, au moment où vous l’entrez. Les évaluations suivantes sont désactivées. Vous pouvez substituer manuellement ce comportement en cliquant sur l’icône de mise à jour qui s’affiche à côté de la valeur.  
  
 Une façon d’éviter tous les effets secondaires est de désactiver l’évaluation de fonction automatique (**Outils/Options/Débogage/Activer l'évaluation de la propriété et d’autres appels de fonction implicite**).  
  
 Quand l’évaluation des propriétés ou des appels de fonctions implicites est désactivée, vous pouvez forcer l’évaluation en utilisant le modificateur de format **ac** (pour C# uniquement). Consultez [Format Specifiers in C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Utilisation d’ID d’objet dans la fenêtre Espion (C# et Visual Basic)  
 Vous pouvez parfois être amené à observer le comportement d’un objet spécifique. Par exemple, vous pouvez souhaiter suivre un objet référencé par une variable locale devenue hors de portée. En C# et Visual Basic, vous pouvez créer des ID d’objet pour des instances spécifiques de types de références et les utiliser dans la fenêtre Espion et dans les conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.  
  
> [!NOTE]
>  Les ID d’objet créent des références faibles et n’empêchent pas l’objet de subir une récupération de mémoire. Leur validité ne vaut que pour la session de débogage active.  
  
 Dans le code suivant, une méthode crée une personne ( `Person` ) en utilisant une variable locale, mais vous voulez déterminer le nom de `Person`dans une autre méthode :  
  
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
    List<Person> _people = new List<Person>();  
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
  
1.  Définissez un point d’arrêt dans le code quelque temps après que l’objet a été créé.  
  
2.  Démarrez le débogage et quand l’exécution s’interrompt au point d’arrêt, recherchez la variable dans la fenêtre **Variables locales** , cliquez dessus avec le bouton droit, puis sélectionnez **Générer ID de l’objet**.  
  
3.  Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Il s’agit de l’ID d’objet.  
  
4.  Ajoutez l’ID d’objet à la fenêtre Espion.  
  
5.  Définissez un point d’arrêt là où vous voulez observer le comportement de l’objet.  Dans le code ci-dessus, ce serait dans la méthode `DoSomething()` .  
  
6.  Poursuivez le débogage et quand l’exécution s’arrête dans la méthode `DoSomething()` , la fenêtre **Espion** affiche l’objet `Person` .  
  
> [!NOTE]
>  Si vous voulez afficher les propriétés de l’objet, telles que `Person.Name` dans l’exemple ci-dessus, vous devez avoir activé l’évaluation de propriété.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Utilisation de registres dans la fenêtre Espion (C++ uniquement)  
 Si vous déboguez du code natif, vous pouvez ajouter des noms de registres, ainsi que les noms de variables à l’aide de  **$ \<inscrire nom >** ou  **@ \<inscrire nom >**.  Pour plus d’informations, consultez [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>Affichage dynamique et fenêtre Espion  
 Certains langages de script (par exemple, JavaScript ou Python) utilisent le [typage canard](https://en.wikipedia.org/wiki/Duck_typing)ou dynamique, et les langages .NET (version 4.0 et ultérieures) prennent en charge les objets difficiles à observer dans les fenêtres de débogage normales, car certaines de leurs propriétés ou méthodes d’exécution peuvent ne pas s’afficher.  
  
 Lorsque la fenêtre Espion affiche un objet créé à partir d’un type qui implémente le <xref:System.Dynamic.IDynamicMetaObjectProvider>, le débogueur ajoute un spécial **affichage dynamique** nœud à la **automatique** afficher. Ce nœud affiche les membres dynamiques de l’objet dynamique, mais n’autorise pas la modification des valeurs des membres.  
  
 Si vous cliquez avec le bouton droit sur l’un des enfants d’un **Affichage dynamique** et que vous choisissez **Ajouter un espion**, le débogueur insère une nouvelle variable espion qui effectue le transtypage d’un objet vers un objet dynamique. En d’autres termes, **object Name** devient (**(dynamic)object).Name**.  
  
 L’évaluation des membres d’un **Affichage dynamique** peut avoir des effets secondaires. Pour plus d’informations sur ces effets secondaires, consultez [Side Effects and Expressions](#bkmk_sideEffects). Pour C#, le débogueur ne réévalue pas automatiquement les valeurs présentées dans l’ **Affichage dynamique** quand vous passez à une nouvelle ligne de code. Pour Visual Basic, les expressions ajoutées via l’ **Affichage dynamique** sont automatiquement actualisées.  
  
 Pour obtenir des instructions sur l’actualisation des valeurs de l’Affichage dynamique, consultez [Actualisation des valeurs obsolètes dans la fenêtre Espion](#bkmk_refreshWatch).  
  
 Si vous voulez afficher uniquement l’ **Affichage dynamique** pour un objet, vous pouvez utiliser le spécificateur de format **dynamic** :  
  
- C# : **ObjectName, dynamic**  
  
- Visual Basic:: **$dynamic, ObjectName**  
  
  Par ailleurs, l’ **Affichage dynamique** améliore l’expérience de débogage pour les objets COM. Quand le débogueur rencontre un objet COM encapsulé dans **System.__ComObject**, il ajoute un nœud **Affichage dynamique** pour l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres du débogueur](../debugger/debugger-windows.md)
