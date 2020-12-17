---
title: Assertions dans du code managé | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 824c711fc0ebb26a78338a65808c6fdbed768919
ms.sourcegitcommit: fed8782b2fb2ca18a90746b6e7e0b33f3fde10f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97646396"
---
# <a name="assertions-in-managed-code"></a>Assertions dans du code managé
Une assertion, ou instruction `Assert`, teste une condition, que vous spécifiez en tant qu'argument à l'instruction `Assert`. Si la condition a la valeur true, aucune action ne se produit. Si la condition a la valeur false, l'assertion échoue. S'il est exécuté avec une version Debug, votre programme passe en mode arrêt.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique
 [Assertions dans l’espace de noms System. Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Méthode Debug. Assert](#BKMK_The_Debug_Assert_method)

 [Effets secondaires de Debug. Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Exigences de trace et de débogage](#BKMK_Trace_and_Debug_Requirements)

 [Arguments Assert](#BKMK_Assert_arguments)

 [Personnalisation du comportement d’Assert](#BKMK_Customizing_Assert_behavior)

 [Définition d’assertions dans les fichiers de configuration](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Assertions dans l’espace de noms System.Diagnostics
 En Visual Basic et Visual C#, vous pouvez utiliser la méthode `Assert` de <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace>, qui est dans l'espace de noms <xref:System.Diagnostics>. Les méthodes de la classe <xref:System.Diagnostics.Debug> ne sont pas incluses dans une version Release de votre programme ; par conséquent, elles n’augmentent pas la taille ou ne réduisent pas la vitesse de votre code de version Release.

 C++ ne prend pas en charge les méthodes de classe <xref:System.Diagnostics.Debug>. Vous pouvez obtenir le même effet en utilisant la classe <xref:System.Diagnostics.Trace> avec la compilation conditionnelle, telle que `#ifdef DEBUG`... `#endif`.

 [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Méthode Debug.Assert
 Utilisez librement la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> pour tester les conditions qui doivent avoir la valeur true si votre code est correct. Par exemple, si vous avez écrit une fonction de division d'entier. Selon les règles mathématiques, le diviseur ne peut pas être égal à zéro. Vous pouvez tester cela en utilisant une assertion :

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
{
    Debug.Assert ( divisor != 0 );
    return ( dividend / divisor );
}
```

 Lorsque vous exécutez ce code sous le débogueur, l'instruction d'assertion est évaluée, mais dans la version Release, la comparaison n'est pas faite, donc il n'y a pas de charge mémoire supplémentaire.

 Voici un autre exemple. Vous avez une classe qui implémente un compte courant de la manière suivante :

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Avant de retirer de l'argent du compte, vous voulez vous assurer que le crédit de votre compte est suffisant pour couvrir la somme que vous allez retirer. Vous pouvez écrire une assertion pour contrôler le solde :

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Notez que les appels à la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> disparaissent lorsque vous créez une version Release de votre code. Cela signifie que l’appel qui vérifie l’équilibre disparaît dans la version Release. Pour résoudre ce problème, remplacez <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> par <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, qui ne disparaît pas dans la version Release :

 Les appels à <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, contrairement aux appels à <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, ajoutent une charge mémoire à la version Release.

 [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Effets secondaires de Debug.Assert
 Lorsque vous utilisez <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, veillez à ce qu'aucun code dans `Assert` ne change les résultats du programme si `Assert` est supprimé. Sinon, vous pouvez par accident introduire un bogue qui ne se produira que dans la version Release de votre programme. Soyez particulièrement vigilant avec les instructions Assert qui contiennent des appels de fonction ou de procédure, comme par exemple dans l'exemple suivant :

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Cette utilisation de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> peut sembler sûre à première vue, mais supposons que la fonction meas mette à jour un compteur à chaque fois qu'elle est appelée. Lorsque vous générez la version Release, cet appel à meas est éliminé, et le compteur ne sera pas mis à jour. Il s'agit d'un exemple d'une fonction avec un effet secondaire. L’élimination d’un appel à une fonction qui a un effet secondaire peut générer un bogue qui n’apparaît que dans la version Release. Pour éviter ce genre de problèmes, ne placez pas d'appels de fonction dans une instruction <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>. Utilisez une variable temporaire à la place :

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 Même lorsque vous utilisez <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, vous pouvez toujours vouloir éviter de placer des appels de fonction dans une instruction `Assert`. Ces appels doivent être sécurisés, car les instructions <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ne sont pas éliminées dans une version Release. Cependant, si vous évitez ces constructions en règle générale, vous ferez moins d'erreurs lors de l'utilisation de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

 [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements"></a> Exigences relatives à Trace et Debug
 Si vous créez votre projet en utilisant les Assistants [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], le symbole TRACE est défini par défaut dans les configurations Release et Debug. Le symbole DEBUG est défini par défaut uniquement dans la version Debug.

 Sinon, pour que les méthodes <xref:System.Diagnostics.Trace> fonctionnent, votre programme doit avoir l'un des éléments suivants en haut du fichier source :

- `#Const TRACE = True` en Visual Basic

- `#define TRACE` en Visual C# et C++

  Ou votre programme doit être généré avec l'option TRACE :

- `/d:TRACE=True` en Visual Basic

- `/d:TRACE` en Visual C# et C++

  Si vous avez besoin d’utiliser les méthodes Debug dans une version Release C# ou Visual Basic, vous devez définir le symbole DEBUG dans votre configuration Release.

  C++ ne prend pas en charge les méthodes de classe <xref:System.Diagnostics.Debug>. Vous pouvez obtenir le même effet en utilisant la classe <xref:System.Diagnostics.Trace> avec la compilation conditionnelle, telle que `#ifdef DEBUG`... `#endif`. Vous pouvez définir ces symboles dans la boîte de dialogue **\<Project> pages de propriétés** . Pour plus d’informations, consultez [Modification des paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) ou [Modification des paramètres de projet pour une configuration Debug C ou C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> Arguments Assert
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> et <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> utilisent trois arguments au maximum. Le premier argument, qui est obligatoire, est la condition que vous souhaitez vérifier. Si vous appelez <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> ou <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> avec un seul argument, la méthode `Assert` vérifie la condition et, si le résultat est false, renvoie le contenu de la pile des appels dans la fenêtre **Sortie**. L'exemple suivant affiche <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> et <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> :

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Le deuxième et le troisième arguments, s’ils sont présents, doivent être des chaînes. Si vous appelez <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> avec deux ou trois arguments, le premier argument est une condition. La méthode vérifie la condition et, si le résultat est false, renvoie les deuxième et troisième chaînes. L’exemple suivant montre <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> utilisés avec deux arguments.

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 L'exemple suivant affiche <xref:System.Diagnostics.Debug.Assert%2A> et <xref:System.Diagnostics.Trace.Assert%2A> :

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> Personnalisation du comportement d’assertion
 Si vous exécutez votre application en mode interface utilisateur, la méthode `Assert` affiche la boîte de dialogue **Échec de l’assertion** quand la condition échoue. Les actions qui se produisent lors de l’échec d’une assertion sont contrôlées par la propriété <xref:System.Diagnostics.Debug.Listeners%2A> ou la propriété <xref:System.Diagnostics.Trace.Listeners%2A>.

 Vous pouvez personnaliser le comportement en sortie en ajoutant un objet <xref:System.Diagnostics.TraceListener> à la collection `Listeners`, en supprimant un <xref:System.Diagnostics.TraceListener> de la collection `Listeners` ou en substituant la méthode <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> par un `TraceListener` existant pour modifier son comportement.

 Par exemple, vous pouvez substituer la méthode <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> pour écrire dans un journal des événements au lieu d’afficher la boîte de dialogue **Échec de l’assertion**.

 Pour personnaliser la sortie de cette façon, votre programme doit contenir un écouteur et vous devez hériter de <xref:System.Diagnostics.TraceListener> et substituer sa méthode <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>.

 Pour plus d’informations, consultez [écouteurs de suivi](/dotnet/framework/debug-trace-profile/trace-listeners).

 [Dans cette rubrique](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Définition d’assertions dans les fichiers de configuration
 Vous pouvez définir des assertions dans le fichier de configuration de votre programme ainsi que dans votre code. Pour plus d'informations, consultez <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Traçage et instrumentation d’applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Procédure : Effectuer une compilation conditionnelle avec Trace et Debug](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)