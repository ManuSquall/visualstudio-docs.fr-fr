---
title: 'Ca2172 : Évitez de gérer les exceptions d’état endommagé | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 27d837c09e5f2f90796c149bf58d1114d7e6352d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546313"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153 : Éviter la gestion des exceptions d’état endommagé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Les[exceptions d’état endommagé (CSE, Corrupted State Exceptions)](https://msdn.microsoft.com/magazine/dd419661.aspx) indiquent une altération de la mémoire dans votre processus. Le fait d’intercepter ces exceptions au lieu d’autoriser le processus à se bloquer peut engendrer des failles de sécurité si une personne malveillante réussit à placer une attaque dans la région de la mémoire endommagée.

## <a name="rule-description"></a>Description de la règle
 Les CSE indiquent que l’état d’un processus a été endommagé et qu’il n’a pas été intercepté par le système. Dans un scénario d’état endommagé, un gestionnaire général intercepte uniquement l’exception si votre méthode est marquée au moyen de l’attribut `HandleProcessCorruptedStateExceptions` approprié. Par défaut, le [Common Language Runtime (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) n’appelle pas les gestionnaires catch pour les CSE.

 L’option la plus sûre consiste à autoriser le blocage du processus sans intercepter ces types d’exceptions, dans la mesure où même le code de journalisation peut permettre à des personnes malveillantes d’exploiter les bogues d’endommagement de la mémoire.

 Cet avertissement se déclenche lors de l’interception de CSE au moyen d’un gestionnaire général qui intercepte toutes les exceptions, notamment catch(exception) ou catch(aucune exception spécifiée).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cet avertissement, vous devez effectuer l’une des opérations suivantes :

 1. Supprimez l'attribut `HandleProcessCorruptedStateExceptions`. Cela a pour effet de rétablir le comportement du runtime par défaut selon lequel les CSE ne sont pas passées aux gestionnaires catch.

 2. Supprimer le gestionnaire catch général et privilégier les gestionnaires qui interceptent des types d’exceptions spécifiques.  Cela peut inclure des CSE si le code du gestionnaire arrive à les gérer en toute sécurité (ce qui est très rare).

 3. Lever à nouveau l’exception CSE dans le gestionnaire catch pour garantir le passage de l’exception à l’appelant et l’arrêt consécutif du processus en cours d’exécution.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

### <a name="violation"></a>Violation
 Le pseudo-code suivant illustre le modèle détecté par cette règle.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Solution 1
 Supprimez l’attribut HandleProcessCorruptedExceptions pour faire en sorte que les exceptions ne soient pas gérées.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Solution 2
 Supprimez le gestionnaire catch général et interceptez uniquement des types d’exceptions spécifiques.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Solution 3
 Levez à nouveau l’exception.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```
