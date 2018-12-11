---
title: Gérer les exceptions avec le débogueur Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f19bbbfbde9a111c6edea112b7250fca934ac7f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881688"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gérer les exceptions avec le débogueur dans Visual Studio

Une exception est une indication d'un état d'erreur qui se produit pendant qu'un programme est en cours d'exécution. Vous pouvez demander au débogueur les exceptions ou les ensembles d’exceptions pour rompre sur, et à quel point vous voulez le débogueur s’arrête. Lorsque le débogueur s’arrête, il vous montre où l’exception a été levée. Vous pouvez également ajouter ou supprimer des exceptions. Avec une solution ouverte dans Visual Studio, utilisez **Déboguer > Windows > Paramètres d’Exception** pour ouvrir le **paramètres d’Exception** fenêtre.

Fournir des gestionnaires qui répondent aux exceptions plus importantes. Découvrez également comment configurer le débogueur pour toujours arrêter l’exécution pour certaines exceptions.

Lorsqu’une exception se produit, le débogueur écrit un message d’exception à la **sortie** fenêtre. Cette action peut interrompre l’exécution dans l’exemple suivant cas quand :

- Une exception est levée qui n’est pas gérée.
- Le débogueur est configuré pour arrêter l’exécution avant tout gestionnaire est appelé.
- Vous avez défini [uniquement mon Code](../debugger/just-my-code.md), et le débogueur est configuré pour s’arrêter sur toute exception qui n’est pas gérée dans le code utilisateur.

> [!NOTE]
> ASP.NET a un gestionnaire d'exceptions de niveau supérieur qui affiche les pages d'erreur dans un navigateur. Il n’interrompt l’exécution, sauf si **uniquement mon Code** est activé. Pour obtenir un exemple, consultez [demander au débogueur de continuer en cas d’exceptions non gérées par l’utilisateur](#BKMK_UserUnhandled) ci-dessous.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Dans une application Visual Basic, le débogueur gère toutes les erreurs en tant qu’exceptions, même si vous utilisez sur les gestionnaires d’erreurs de style d’erreur.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indiquer le débogueur s’arrête lorsqu’une exception est levée.

Le débogueur peut arrêter l’exécution au point où une exception est levée, donc vous pouvez examiner l’exception avant un gestionnaire est appelé.

Dans le **paramètres d’Exception** fenêtre (**Déboguer > Windows > Paramètres d’Exception**), développez le nœud d’une catégorie d’exceptions, tel que **Exceptions Common Language Runtime**. Puis sélectionnez la case à cocher pour une exception spécifique de cette catégorie, comme **System.AccessViolationException**. Vous pouvez également sélectionner une catégorie entière d'exceptions.

![Vérifié AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Vous pouvez trouver des exceptions spécifiques à l’aide de la **recherche** fenêtre dans le **paramètres d’Exception** barre d’outils, ou utilisez recherche pour filtrer des espaces de noms spécifiques (telles que **System.IO**).

Si vous sélectionnez une exception dans le **paramètres d’Exception** fenêtre, l’exécution du débogueur s’arrête chaque fois que l’exception est levée, peu importe si elle est gérée. L’exception est devenue une exception de première chance. Voici, par exemple, quelques scénarios :

- Dans l’application de console c# suivante, la méthode Main lève une **AccessViolationException** à l’intérieur d’un `try/catch` bloc.

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

  Si vous avez **AccessViolationException** archivé **paramètres d’Exception**, l’exécution s’arrête sur la `throw` lorsque vous exécutez ce code dans le débogueur de ligne. Vous pouvez ensuite poursuivre l'exécution. La console devrait afficher les deux lignes :

  ```cmd
  caught exception
  goodbye
  ```

  mais il n’affiche pas le `here` ligne.

- Une application de console c# fait référence à une bibliothèque de classes avec une classe qui possède deux méthodes. Une méthode lève une exception et prend en charge, tandis que d’une deuxième méthode lève la même exception mais ne la gère.

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

  Voici la méthode Main() de l’application de console :

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Si vous avez **AccessViolationException** archivé **paramètres d’Exception**, l’exécution s’arrête sur la `throw` ligne dans les deux **ThrowHandledException()** et **ThrowUnhandledException()** lorsque vous exécutez ce code dans le débogueur.

Pour restaurer les paramètres d’exception pour les valeurs par défaut, choisissez le **restaurer la liste les paramètres par défaut** bouton :

![Restaurer les valeurs par défaut dans les paramètres d’Exception](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Demander au débogueur de continuer en cas d’exceptions non gérées par l’utilisateur

Si vous déboguez du code .NET ou JavaScript avec [uniquement mon Code](../debugger/just-my-code.md), vous pouvez demander au débogueur pour empêcher l’arrêt sur les exceptions qui ne sont pas gérées dans le code utilisateur, mais sont gérées ailleurs.

1. Dans le **paramètres d’Exception** fenêtre, ouvrez le menu contextuel en cliquant sur une étiquette de colonne, puis sélectionnez **afficher les colonnes > des Actions supplémentaires**. (Si vous avez désactivé **uniquement mon Code**, vous ne voyez pas cette commande.) Une troisième colonne nommée **des Actions supplémentaires** s’affiche.

   ![Colonne d’Actions supplémentaire](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Pour une exception indiquant **continuer en cas d’exception non gérée dans le code utilisateur** dans cet article, le débogueur continue si cette exception n’est pas gérée dans le code utilisateur, mais est gérée en externe.

2. Pour modifier ce paramètre pour une exception spécifique, sélectionnez l’exception, avec le bouton droit pour afficher le menu contextuel, puis **continuer lorsque exception non gérée dans le Code utilisateur**. Vous pouvez également modifier le paramètre pour une catégorie entière d’exceptions, telles que les exceptions Common Language Runtime entières).

   ![** Continuer en cas d’exception non gérée dans le paramètre code ** utilisateur](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Par exemple, les applications web ASP.NET gèrent les exceptions en les convertissant en un code d’état HTTP 500 ([gestion des exceptions dans ASP.NET Web API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), qui ne peut pas vous aider à déterminer la source de l’exception. Dans l'exemple ci-dessous, le code utilisateur appelle `String.Format()` qui lève une exception <xref:System.FormatException>. L'exécution s'interrompt de la façon suivante :

![S’arrête sur utilisateur&#45;exception non gérée](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Ajouter et supprimer des exceptions

Vous pouvez ajouter et supprimer des exceptions. Pour supprimer un type d’exception à partir d’une catégorie, sélectionnez l’exception, puis choisissez le **supprimer l’exception sélectionnée dans la liste** bouton (signe moins) sur le **paramètres d’Exception** barre d’outils. Soit l’exception d’avec le bouton droit et sélectionnez **supprimer** dans le menu contextuel. La suppression d’une exception a le même effet que si l’exception est désactivée, c'est-à-dire que le débogueur ne s’arrête lorsqu’elle est levée.

Pour ajouter une exception :

1. Dans le **paramètres d’Exception** fenêtre, sélectionnez une des catégories d’exception (par exemple, **Common Language Runtime**).

2. Choisissez le **ajouter une exception à la catégorie sélectionnée** bouton (signe plus).

   ![** Ajouter une exception au bouton sélectionné catégorie **](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Tapez le nom de l’exception (par exemple, **System.UriTemplateMatchException**).

   ![Tapez le nom de l’exception](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   L’exception est ajoutée à la liste (par ordre alphabétique) et automatiquement activée.

Pour ajouter une exception pour les Exceptions d’accès mémoire GPU, Exceptions du Runtime JavaScript ou des catégories d’Exceptions Win32, incluez le code d’erreur et la description.

> [!TIP]
> Vérifiez l'orthographe. Le **paramètres d’Exception** fenêtre ne vérifie pas l’existence d’une exception ajoutée. Par conséquent, si vous tapez **Sytem.UriTemplateMatchException**, vous obtenez une entrée pour cette exception (et non pour **System.UriTemplateMatchException**).

Paramètres d’exception sont conservés dans le fichier .suo de la solution, et s’appliquent à une solution spécifique. Vous ne pouvez pas réutiliser les paramètres d’exception spécifique sur les solutions. Maintenant seulement les exceptions ajoutées sont conservées ; exceptions supprimées ne sont pas. Vous pouvez ajouter une exception, fermez et rouvrez la solution, et l’exception sera toujours présente. Mais si vous supprimez une exception et que vous fermez/rouvrez la solution, l'exception ne s'affiche plus.

La fenêtre **Paramètres d'exception** prend en charge les types d'exceptions génériques en C#, mais pas en Visual Basic. Pour effectuer un arrêt sur des exceptions telles que `MyNamespace.GenericException<T>`, vous devez ajouter l'exception en tant que **MyNamespace.GenericException'1**. Autrement dit, si vous avez créé une exception semblable à ce code :

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Vous pouvez ajouter l’exception à **paramètres d’Exception** à l’aide de la procédure précédente :

![Ajout d’une exception générique](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Ajouter des conditions à une exception

Utilisez le **paramètres d’Exception** fenêtre pour définir des conditions sur les exceptions. Conditions actuellement pris en charge incluent les noms de module à inclure ou exclure de l’exception. En définissant des noms de module en tant que conditions, vous pouvez choisir Arrêter l’exécution de l’exception uniquement sur certains des modules de code. Vous pouvez également choisir d’éviter l’arrêt sur les modules particuliers.

> [!NOTE]
> Ajout de conditions à une exception est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Pour ajouter des exceptions conditionnelles :

1. Choisissez le **modifier les conditions** bouton dans la fenêtre Paramètres d’Exception, ou avec le bouton droit de l’exception et choisissez **modifier les Conditions**.

   ![Conditions pour une exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Pour ajouter des conditions supplémentaires requises à l’exception, sélectionnez **ajouter une Condition** pour chaque nouvelle condition. Lignes de la condition supplémentaire s’affichent.

   ![Conditions supplémentaires pour une exception](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pour chaque ligne de la condition, tapez le nom du module et modifier la liste d’opérateurs de comparaison à **est égal à** ou **n’est pas égal**. Vous pouvez spécifier des caractères génériques (**\\***) dans le nom pour spécifier plusieurs modules.

4. Si vous avez besoin supprimer une condition, choisissez le **X** à la fin de la ligne de la condition.

## <a name="see-also"></a>Voir aussi

[Poursuivre l’exécution après une exception](../debugger/continuing-execution-after-an-exception.md)<br/>
[Guide pratique pour examiner un code système après une exception](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Utiliser des contrôles d’exécution sans la bibliothèque Runtime C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Didacticiel : Apprenez à déboguer à l’aide de Visual Studio](../debugger/getting-started-with-the-debugger.md)
