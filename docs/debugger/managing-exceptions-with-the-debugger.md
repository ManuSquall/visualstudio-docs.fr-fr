---
title: Gérer les exceptions avec le débbuggeur . Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302153"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gérer les exceptions avec le débbugger dans Visual Studio

Une exception est une indication d'un état d'erreur qui se produit pendant qu'un programme est en cours d'exécution. Vous pouvez dire au débbugger quelles exceptions ou ensembles d’exceptions à briser, et à quel point vous voulez que le débbugger de briser (c’est-à-dire, pause dans le débbugger). Lorsque le débbuggeur se brise, il vous montre où l’exception a été jetée. Vous pouvez également ajouter ou supprimer des exceptions. Avec une solution ouverte dans Visual Studio, utilisez **Debug > Windows > Paramètres d’exception** pour ouvrir la fenêtre **Des paramètres d’exception.**

Fournir des gestionnaires qui répondent aux exceptions les plus importantes. Si vous avez besoin de savoir comment ajouter des gestionnaires pour des exceptions, voir [bugs Fix en écrivant un meilleur code C .](../debugger/write-better-code-with-visual-studio.md) Aussi, apprendre à configurer le débbuggeur pour toujours briser l’exécution pour certaines exceptions.

Lorsqu’une exception se produit, le débbuggeur écrit un message d’exception à la fenêtre **de sortie.** Il peut briser l’exécution dans les cas suivants lorsque :

- Une exception est lancée qui n’est pas manipulée.
- Le débbuggeur est configuré pour briser l’exécution avant qu’un gestionnaire ne soit invoqué.
- Vous avez défini [Just My Code](../debugger/just-my-code.md), et le débbuggeur est configuré pour casser sur toute exception qui n’est pas traitée dans le code utilisateur.

> [!NOTE]
> ASP.NET a un gestionnaire d'exceptions de niveau supérieur qui affiche les pages d'erreur dans un navigateur. Il ne rompt pas l’exécution à moins que **Just My Code** ne soit activé. Par exemple, voir [Dites au débogénaire de continuer sur les exceptions non gérées par l’utilisateur ci-dessous.](#BKMK_UserUnhandled)

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Dans une application Visual Basic, le débogueur gère toutes les erreurs comme des exceptions, même si vous utilisez des gestionnaires d’erreurs de style « en cas d’erreur ».

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Dites au débogénaire de se casser lorsqu’une exception est lancée

Le débbuggeur peut briser l’exécution au point où une exception est lancée, de sorte que vous pouvez examiner l’exception avant qu’un gestionnaire soit invoqué.

Dans la fenêtre **Paramètres d’exception** (**Debug > Windows > Paramètres d’exception**), étendre le nœud pour une catégorie d’exceptions, telles que **common Language Runtime Exceptions**. Sélectionnez ensuite la case à cocher pour une exception spécifique dans cette catégorie, telle que **System.AccessViolationException**. Vous pouvez également sélectionner une catégorie entière d'exceptions.

![Exception AccessViolationException vérifiée](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Vous pouvez trouver des exceptions spécifiques en utilisant la fenêtre **de recherche** dans la barre **d’outils Des paramètres d’exception,** ou utiliser la recherche pour filtrer des espaces de nom spécifiques (tels que **System.IO**).

Si vous sélectionnez une exception dans la fenêtre **Paramètres d’exception,** l’exécution des débbuggeurs se brisera partout où l’exception est lancée, peu importe si elle est manipulée. Maintenant, l’exception est appelée une exception de première chance. Voici, par exemple, quelques scénarios :

- Dans l’application de console C suivante, la méthode Main `try/catch` lance un **AccessViolationException** à l’intérieur d’un bloc.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Si vous avez **AccessViolationException** vérifié dans Les `throw` paramètres **d’exception**, l’exécution se brisera sur la ligne lorsque vous exécutez ce code dans le débbugger. Vous pouvez ensuite poursuivre l'exécution. La console devrait afficher les deux lignes :

  ```cmd
  caught exception
  goodbye
  ```

  mais il n’affiche `here` pas la ligne.

- Une application de console CMD fait référence à une bibliothèque de classe avec une classe qui a deux méthodes. Une méthode lance une exception et la gère, tandis qu’une deuxième méthode lance la même exception, mais ne la gère pas.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Voici la méthode Main() de l’application console :

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Si vous avez **AccessViolationException** vérifié dans Les `throw` paramètres **d’exception**, l’exécution se brisera sur la ligne à la fois dans **ThrowHandledException()** et **ThrowUnhandledException()** lorsque vous exécutez ce code dans le débbugger.

Pour restaurer les paramètres d’exception aux par défauts, choisissez la **restauration de la liste sur le** bouton Paramètres par défaut :

![Restaurer les valeurs par défaut dans les paramètres des exceptions](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Dites au débogénaire de continuer sur les exceptions non gérées par l’utilisateur

Si vous débogage .NET ou JavaScript code avec [Just My Code](../debugger/just-my-code.md), vous pouvez dire au débbugger pour éviter de casser sur les exceptions qui ne sont pas traitées dans le code utilisateur, mais sont manipulés ailleurs.

1. Dans la fenêtre **Paramètres d’exception,** ouvrez le menu raccourci en cliquant à droite sur une étiquette de colonne, puis sélectionnez **Des colonnes d’exposition > actions supplémentaires**. (Si vous avez désactivé **Just My Code**, vous ne verrez pas cette commande.) Une troisième colonne nommée **Actions Supplémentaires** apparaît.

   ![Colonne actions supplémentaires](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Pour une exception qui s’affiche **Continuer lorsqu’il n’est pas manipulé dans** le code utilisateur dans cette colonne, le débbuggeur continue si cette exception n’est pas traitée dans le code utilisateur, mais est traitée à l’extérieur.

2. Pour modifier ce paramètre pour une exception particulière, sélectionnez l’exception, cliquez à droite pour afficher le menu raccourci, et **sélectionnez Continuer Lorsque vous n’êtes pas manipulé dans le code utilisateur**. Vous pouvez également modifier le paramètre pour toute une catégorie d’exceptions, telles que l’ensemble des exceptions de temps de course de langue commune).

   ![Continuez lorsqu’il n’est pas manipulé dans le paramètre du code utilisateur](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinuerWhenUnhandledInUserCodeSetting")

Par exemple, ASP.NET applications Web gèrent les exceptions en les convertissant en code de statut HTTP 500[(traitement d’exception dans ASP.NET’API Web](/aspnet/web-api/overview/error-handling/exception-handling)), ce qui peut ne pas vous aider à déterminer la source de l’exception. Dans l'exemple ci-dessous, le code utilisateur appelle `String.Format()` qui lève une exception <xref:System.FormatException>. L'exécution s'interrompt de la façon suivante :

![Pauses sur l’utilisateur&#45;exception non manipulée](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Ajouter et supprimer des exceptions

Vous pouvez ajouter et supprimer des exceptions. Pour supprimer un type d’exception d’une catégorie, sélectionnez l’exception et choisissez **l’exception supprimer la base du** bouton de liste (le signe négatif) sur la barre **d’outils Paramètres d’exception.** Ou vous pouvez cliquer à droite sur l’exception et sélectionner **Supprimer** dans le menu raccourci. Supprimer une exception a le même effet que d’avoir l’exception non contrôlée, c’est-à-dire que le débbuggeur ne se cassera pas quand il est jeté.

Pour ajouter une exception :

1. Dans la fenêtre **Paramètres d’exception,** sélectionnez l’une des catégories d’exception (par exemple, **Common Language Runtime**).

2. Choisissez **l’Ajouter une exception au** bouton de catégorie sélectionné (le signe positif).

   ![Ajouter une exception au bouton de la catégorie sélectionnée](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Tapez le nom de l’exception (par exemple, **System.UriTemplateMatchException**).

   ![Tapez le nom d’exception](../debugger/media/typetheexceptionname.png "TypeTheExceptionName (en anglais)")

   L’exception est ajoutée à la liste (par ordre alphabétique) et automatiquement vérifiée.

Pour ajouter une exception aux exceptions d’accès à la mémoire GPU, javaScript Runtime Exceptions, ou Win32 Exceptions catégories, inclure le code d’erreur et la description.

> [!TIP]
> Vérifiez l'orthographe. La fenêtre **Paramètres d’exception** ne vérifie pas l’existence d’une exception supplémentaire. Donc, si vous tapez **Sytem.UriTemplateMatchException**, vous obtiendrez une entrée pour cette exception (et non pour **System.UriTemplateMatchException**).

Les paramètres d’exception sont conservés dans le fichier .suo de la solution ; ils s’appliquent donc à une solution spécifique. Vous ne pouvez pas réutiliser des paramètres d’exception spécifiques entre plusieurs solutions. Maintenant, seules les exceptions ajoutées persistent; exceptions supprimées ne sont pas. Vous pouvez ajouter une exception, fermer et rouvrir la solution, et l’exception sera toujours là. Mais si vous supprimez une exception et que vous fermez/rouvrez la solution, l'exception ne s'affiche plus.

La fenêtre **Paramètres d'exception** prend en charge les types d'exceptions génériques en C#, mais pas en Visual Basic. Pour effectuer un arrêt sur des exceptions telles que `MyNamespace.GenericException<T>`, vous devez ajouter l'exception en tant que **MyNamespace.GenericException'1**. Autrement dit, si vous avez créé une exception comme ce code:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Vous pouvez ajouter l’exception aux **Paramètres d’exception** à l’aide de la procédure précédente :

![ajout d'une exception générique](../debugger/media/addgenericexception.png "AddGenericException (en anglais)")

## <a name="add-conditions-to-an-exception"></a>Ajouter des conditions à une exception

Utilisez la fenêtre **Paramètres d’exception** pour définir les conditions sur les exceptions. Les conditions actuellement prises en charge comprennent le nom du module pour inclure ou exclure pour l’exception. En définissant les noms du module comme conditions, vous pouvez choisir de casser pour l’exception uniquement sur certains modules de code. Vous pouvez également choisir d’éviter de casser sur des modules particuliers.

> [!NOTE]
> Ajouter des conditions à une [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]exception est pris en charge à partir de .

Pour ajouter des exceptions conditionnelles :

1. Choisissez le bouton **Conditions d’édition** dans la fenêtre Paramètres d’exception ou cliquez à droite sur l’exception et choisissez **Edit Conditions**.

   ![Conditions d’exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Pour ajouter des conditions supplémentaires requises à l’exception, sélectionnez **Ajouter la condition** pour chaque nouvelle condition. D’autres lignes d’état apparaissent.

   ![Conditions supplémentaires pour une exception](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pour chaque ligne d’état, tapez le nom du module et modifiez la liste de l’opérateur de comparaison en **égaux** ou **non.** Vous pouvez spécifier des wildcards (**\\**) dans le nom pour spécifier plus d’un module.

4. Si vous avez besoin de supprimer une condition, choisissez le **X** à la fin de la ligne d’état.

## <a name="see-also"></a>Voir aussi

- [Poursuivre l’exécution après une exception](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Guide pratique pour examiner un code système après une exception](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Utilisez les vérifications en temps d’exécution sans la bibliothèque C run-time](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Premier regard sur le débbugger](../debugger/debugger-feature-tour.md)
