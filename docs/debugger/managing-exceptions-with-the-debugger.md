---
title: Gérer les exceptions avec le débogueur | Microsoft Docs
description: Découvrez comment spécifier les exceptions sur lesquelles le débogueur s’arrête, à quel moment vous souhaitez que le débogueur s’arrête et comment les sauts sont gérés.
ms.custom: SEO-VS-2020
ms.date: 10/09/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89795df3a4c6b87c6a878cd07a072027f880e660
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390422"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gérer les exceptions avec le débogueur dans Visual Studio

Une exception est une indication d'un état d'erreur qui se produit pendant qu'un programme est en cours d'exécution. Vous pouvez indiquer au débogueur les exceptions ou les jeux d’exceptions sur lesquels s’arrêter, et à quel point vous souhaitez que le débogueur s’arrête (c’est-à-dire, s’il est suspendu dans le débogueur). Quand le débogueur s’arrête, il vous indique où l’exception a été levée. Vous pouvez également ajouter ou supprimer des exceptions. Si une solution est ouverte dans Visual Studio, utilisez les **paramètres de débogage > Windows > les paramètres d’exception** pour ouvrir la fenêtre Paramètres d' **exception** .

Fournissez des gestionnaires qui répondent aux exceptions les plus importantes. Si vous avez besoin de savoir comment ajouter des gestionnaires pour les exceptions, consultez [corriger des bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md). En outre, Découvrez comment configurer le débogueur pour qu’il arrête toujours l’exécution pour certaines exceptions.

Quand une exception se produit, le débogueur écrit un message d’exception dans la fenêtre **sortie** . Elle peut arrêter l’exécution dans les cas suivants :

- Une exception qui n’est pas gérée est levée.
- Le débogueur est configuré pour arrêter l’exécution avant l’appel d’un gestionnaire.
- Vous avez défini [uniquement mon code](../debugger/just-my-code.md), et le débogueur est configuré pour s’arrêter sur toute exception qui n’est pas gérée dans le code utilisateur.

> [!NOTE]
> ASP.NET a un gestionnaire d'exceptions de niveau supérieur qui affiche les pages d'erreur dans un navigateur. Elle n’interrompt pas l’exécution, sauf si **uniquement mon code** est activé. Pour obtenir un exemple, consultez [demander au débogueur de continuer sur les exceptions non gérées par l’utilisateur](#BKMK_UserUnhandled) ci-dessous.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Dans une application Visual Basic, le débogueur gère toutes les erreurs comme des exceptions, même si vous utilisez des gestionnaires d’erreurs de style « en cas d’erreur ».

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indiquer au débogueur d’arrêter lorsqu’une exception est levée

Le débogueur peut arrêter l’exécution au point où une exception est levée. vous pouvez donc examiner l’exception avant qu’un gestionnaire soit appelé.

Dans la fenêtre **paramètres d’exception** (**déboguer > paramètres d’exception Windows >**), développez le nœud d’une catégorie d’exceptions, par exemple, **exceptions du Common Language Runtime**. Activez ensuite la case à cocher d’une exception spécifique au sein de cette catégorie, par exemple **System. AccessViolationException**. Vous pouvez également sélectionner une catégorie entière d'exceptions.

![Exception AccessViolationException vérifiée](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Vous pouvez trouver des exceptions spécifiques à l’aide de la fenêtre **Rechercher** de la barre d’outils **paramètres d’exception** , ou utiliser la fonction de recherche pour filtrer des espaces de noms spécifiques (par exemple, **System.IO**).

Si vous sélectionnez une exception dans la fenêtre **paramètres d’exception** , l’exécution du débogueur s’arrête partout où l’exception est levée, peu importe si elle est gérée. L’exception est maintenant appelée une exception de première chance. Voici, par exemple, quelques scénarios :

- Dans l’application console C# suivante, la méthode main lève une **AccessViolationException** à l’intérieur d’un `try/catch` bloc.

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

  Si **AccessViolationException** a archivé des **paramètres d’exception**, l’exécution s’arrête sur la `throw` ligne quand vous exécutez ce code dans le débogueur. Vous pouvez ensuite poursuivre l'exécution. La console devrait afficher les deux lignes :

  ```cmd
  caught exception
  goodbye
  ```

  mais elle n’affiche pas la `here` ligne.

- Une application console C# fait référence à une bibliothèque de classes avec une classe qui a deux méthodes. Une méthode lève une exception et la gère, tandis qu’une deuxième méthode lève la même exception, mais ne la gère pas.

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

  Si **AccessViolationException** a archivé des **paramètres d’exception**, l’exécution s’arrête sur la `throw` ligne dans **ThrowHandledException ()** et **dans throwunhandledexception ()** lorsque vous exécutez ce code dans le débogueur.

Pour rétablir les valeurs par défaut des paramètres d’exception, choisissez le bouton **restaurer la liste sur les paramètres par défaut** :

![Restaurer les valeurs par défaut dans les paramètres des exceptions](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Indiquer au débogueur de continuer sur les exceptions non gérées par l’utilisateur

Si vous déboguez du code .NET ou JavaScript avec [uniquement mon code](../debugger/just-my-code.md), vous pouvez indiquer au débogueur d’empêcher la rupture sur les exceptions qui ne sont pas gérées dans le code utilisateur, mais qui sont gérées ailleurs.

1. Dans la fenêtre **paramètres d’exception** , ouvrez le menu contextuel en cliquant avec le bouton droit sur une étiquette de colonne, puis sélectionnez Afficher les **colonnes > Actions supplémentaires**. (Si vous avez désactivé **uniquement mon code**, vous ne verrez pas cette commande.) Une troisième colonne nommée **actions supplémentaires** s’affiche.

   ![Colonne actions supplémentaires](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Pour une exception qui affiche continue lorsqu’elle n’est pas **gérée dans le code utilisateur** de cette colonne, le débogueur continue si cette exception n’est pas gérée dans le code utilisateur, mais est gérée en externe.

2. Pour modifier ce paramètre pour une exception particulière, sélectionnez l’exception, cliquez avec le bouton droit pour afficher le menu contextuel, puis sélectionnez **Continuer en cas d’exception non gérée dans le code utilisateur**. Vous pouvez également modifier le paramètre pour une catégorie entière d’exceptions, telles que l’ensemble des exceptions du Common Language Runtime).

   ![* * Continuer en cas d’exception non gérée dans le code utilisateur * *](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Par exemple, les applications Web ASP.NET gèrent les exceptions en les convertissant en code d’état HTTP 500 ([gestion des exceptions dans API Web ASP.net](/aspnet/web-api/overview/error-handling/exception-handling)), ce qui peut ne pas vous aider à déterminer la source de l’exception. Dans l'exemple ci-dessous, le code utilisateur appelle `String.Format()` qui lève une exception <xref:System.FormatException>. L'exécution s'interrompt de la façon suivante :

![Interruptions sur l’utilisateur&#45;exception non gérée](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Ajouter et supprimer des exceptions

Vous pouvez ajouter et supprimer des exceptions. Pour supprimer un type d’exception d’une catégorie, sélectionnez l’exception, puis choisissez l’option **Supprimer l’exception sélectionnée dans la liste** (le signe moins) dans la barre d’outils **paramètres d’exception** . Vous pouvez également cliquer avec le bouton droit sur l’exception et sélectionner **supprimer** dans le menu contextuel. La suppression d’une exception a le même effet que si l’exception est désactivée, ce qui indique que le débogueur ne s’arrête pas lorsqu’elle est levée.

Pour ajouter une exception :

1. Dans la fenêtre **paramètres d’exception** , sélectionnez l’une des catégories d’exception (par exemple, **Common Language Runtime**).

2. Choisissez le bouton **Ajouter une exception au bouton catégorie sélectionnée** (le signe plus).

   ![* * Ajouter une exception au bouton * * de la catégorie sélectionnée](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Tapez le nom de l’exception (par exemple, **System. UriTemplateMatchException**).

   ![Tapez le nom de l’exception](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   L’exception est ajoutée à la liste (par ordre alphabétique) et automatiquement activée.

Pour ajouter une exception aux catégories exceptions d’accès mémoire GPU, exceptions du runtime JavaScript ou exceptions Win32, incluez le code d’erreur et la description.

> [!TIP]
> Vérifiez l'orthographe. La fenêtre **paramètres d’exception** ne vérifie pas l’existence d’une exception ajoutée. Par conséquent, si vous tapez System **. UriTemplateMatchException**, vous obtenez une entrée pour cette exception (et non pour **System. UriTemplateMatchException**).

Les paramètres d’exception sont conservés dans le fichier .suo de la solution ; ils s’appliquent donc à une solution spécifique. Vous ne pouvez pas réutiliser des paramètres d’exception spécifiques entre plusieurs solutions. Désormais, seules les exceptions ajoutées sont conservées ; les exceptions supprimées ne le sont pas. Vous pouvez ajouter une exception, fermer et rouvrir la solution, et l’exception sera toujours présente. Mais si vous supprimez une exception et que vous fermez/rouvrez la solution, l'exception ne s'affiche plus.

La fenêtre **Paramètres d'exception** prend en charge les types d'exceptions génériques en C#, mais pas en Visual Basic. Pour effectuer un arrêt sur des exceptions telles que `MyNamespace.GenericException<T>`, vous devez ajouter l'exception en tant que **MyNamespace.GenericException'1**. Autrement dit, si vous avez créé une exception telle que celle-ci :

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Vous pouvez ajouter l’exception aux **paramètres d’exception** à l’aide de la procédure précédente :

![ajout d'une exception générique](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Ajouter des conditions à une exception

Utilisez la fenêtre **paramètres d’exception** pour définir des conditions sur les exceptions. Les conditions actuellement prises en charge incluent les noms de modules à inclure ou exclure pour l’exception. En définissant des noms de module en tant que conditions, vous pouvez choisir d’arrêter l’exception uniquement sur certains modules de code. Vous pouvez également choisir d’éviter une rupture sur des modules particuliers.

> [!NOTE]
> L’ajout de conditions à une exception est pris en charge à partir de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Pour ajouter des exceptions conditionnelles :

1. Choisissez le bouton **modifier les conditions** dans la fenêtre Paramètres d’exception, ou cliquez avec le bouton droit sur l’exception et choisissez Modifier les **conditions**.

   ![Conditions pour une exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Pour ajouter des conditions requises supplémentaires à l’exception, sélectionnez **Ajouter une condition** pour chaque nouvelle condition. Des lignes de condition supplémentaires s’affichent.

   ![Conditions supplémentaires pour une exception](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Pour chaque ligne de condition, tapez le nom du module, puis remplacez la liste d’opérateurs de  comparaison par égal **à ou différent** de. Vous pouvez spécifier des caractères génériques ( **\\\*** ) dans le nom pour spécifier plusieurs modules.

4. Si vous devez supprimer une condition, choisissez la **Croix (X** ) à la fin de la ligne de condition.

## <a name="see-also"></a>Voir aussi

- [Poursuivre l’exécution après une exception](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Guide pratique pour examiner un code système après une exception](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
