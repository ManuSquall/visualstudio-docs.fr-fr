---
title: Règle d’analyse du code CA2153 pour les Exceptions d’état endommagé
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450267"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153 : Éviter la gestion des Exceptions d’état endommagé

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

[Endommagé (CSE) Exceptions d’état](https://msdn.microsoft.com/magazine/dd419661.aspx) indiquent que la mémoire corruption existe dans votre processus. Le fait d’intercepter ces exceptions au lieu d’autoriser le processus à se bloquer peut engendrer des failles de sécurité si une personne malveillante réussit à placer une attaque dans la région de la mémoire endommagée.

## <a name="rule-description"></a>Description de la règle

Les CSE indiquent que l’état d’un processus a été endommagé et qu’il n’a pas été intercepté par le système. Dans le scénario d’état endommagé, un gestionnaire général intercepte uniquement l’exception si vous marquez votre méthode avec le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> attribut. Par défaut, le [Common Language Runtime (CLR)](/dotnet/standard/clr) n’appelle pas de gestionnaires catch pour les CSE.

L’option la plus sûre consiste à autoriser le blocage du processus sans intercepter ces types d’exceptions. Même le code de journalisation peut permettre aux attaquants d’exploiter les bogues de corruption de mémoire.

Cet avertissement se déclenche lors de l’interception de CSE avec un gestionnaire général qui intercepte toutes les exceptions, par exemple, `catch (System.Exception e)` ou `catch` sans paramètre d’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour résoudre cet avertissement, effectuez l’une des opérations suivantes :

- Supprimer l’attribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Cela a pour effet de rétablir le comportement du runtime par défaut selon lequel les CSE ne sont pas passées aux gestionnaires catch.

- Supprimer le gestionnaire catch général et privilégier les gestionnaires qui interceptent des types d’exceptions spécifiques. Cela peut inclure des extensions côté client, en supposant que le code du gestionnaire puisse les gérer en toute sécurité (rare).

- Lever à nouveau l’extension côté client dans le gestionnaire catch, qui passe l’exception à l’appelant et doit entraîner l’arrêt du processus en cours d’exécution.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

### <a name="violation"></a>Violation

Le pseudo-code suivant illustre le modèle détecté par cette règle.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Solution 1 : supprimer l’attribut

Suppression de la <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut garantit que les Exceptions d’état endommagé ne sont pas gérées par votre méthode.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Solution 2 : intercepter des exceptions spécifiques

Supprimez le gestionnaire catch général et interceptez uniquement des types d’exceptions spécifiques.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Solution 3 - rethrow

Lever à nouveau l’exception.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```