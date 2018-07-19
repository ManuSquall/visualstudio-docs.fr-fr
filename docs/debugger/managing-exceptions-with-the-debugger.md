---
title: Gérer les exceptions avec le débogueur Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2017
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
ms.openlocfilehash: 1437728a75e0c6e8babff690bb18c7bd30d3add4
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057468"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gérer les exceptions avec le débogueur dans Visual Studio

Une exception est une indication d'un état d'erreur qui se produit pendant qu'un programme est en cours d'exécution. Vous pouvez demander au débogueur les exceptions (ou ensembles d’exceptions) pour arrêter l’exécution sur, et à quel point vous voulez le débogueur s’arrête (quand le débogueur s’arrête, il vous montre où l’exception a été levée). Vous pouvez également ajouter ou supprimer des exceptions. Avec une solution ouverte dans Visual Studio, utilisez **Déboguer > Windows > Paramètres d’Exception** pour ouvrir le **paramètres d’Exception** fenêtre. 

Vous pouvez et devez fournir des gestionnaires qui répondent aux exceptions plus importantes, mais il est important de savoir comment configurer le débogueur pour toujours arrêter l’exécution pour certaines exceptions.
  
Lorsqu'une exception est levée, le débogueur écrit un message d'exception dans la fenêtre Sortie. Cette action peut interrompre l'exécution dans les cas suivants :  
  
-   lorsqu'une exception est levée et n'est pas gérée ;  
  
-   Lorsque le débogueur est configuré pour arrêter l’exécution avant tout gestionnaire est appelé.  
  
-   Si vous avez défini [uniquement mon Code](../debugger/just-my-code.md), et le débogueur est configuré pour s’arrêter sur toute exception non gérée dans le code utilisateur.  
  
> [!NOTE]
>  ASP.NET a un gestionnaire d'exceptions de niveau supérieur qui affiche les pages d'erreur dans un navigateur. Il n'interrompt pas l'exécution, à moins que l'option **Uniquement mon code** soit activée. Pour obtenir un exemple, consultez [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) , ci-dessous.  
  
> [!NOTE]
>  Dans une application Visual Basic, le débogueur gère toutes les erreurs en tant qu’exceptions, même si vous utilisez sur les gestionnaires d’erreurs de style d’erreur.    
  
## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Indiquer le débogueur s’arrête lorsqu’une exception est levée.  
Le débogueur peut interrompre l'exécution à l'endroit où une exception est levée, ce qui vous permet d'examiner l'exception avant qu'un gestionnaire soit appelé.  
  
Dans le **paramètres d’Exception** fenêtre (**Déboguer > Windows > Paramètres d’Exception**), développez le nœud pour une catégorie d’exceptions (par exemple, **Exceptions Common Language Runtime**, c'est-à-dire les exceptions .NET), puis sélectionnez la case à cocher pour une exception spécifique de cette catégorie (par exemple **System.AccessViolationException**). Vous pouvez également sélectionner une catégorie entière d'exceptions.  
  
![Vérifié AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  

> [!TIP]
> Vous pouvez trouver des exceptions spécifiques à l'aide de la fenêtre **Rechercher** de la barre d'outils **Paramètres d'exception** ou en utilisant la fonction de recherche pour filtrer des espaces de noms spécifiques (par exemple, **System.IO**).
  
Si vous sélectionnez une exception dans le **paramètres d’Exception** fenêtre, l’exécution du débogueur s’arrête chaque fois que l’exception est levée, qu’elle est gérée ou non prise en charge. À ce stade, l'exception est appelée « exception de première chance ». Voici, par exemple, quelques scénarios :  
  
*  Dans l’application de console C# suivante, la méthode Main lève une exception **AccessViolationException** à l’intérieur d’un bloc `try/catch` :  
  
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
  
     Si **AccessViolationException** est cochée dans **Paramètres d'exception**, lorsque vous exécutez ce code dans le débogueur, l’exécution s’arrête à la ligne `throw` . Vous pouvez ensuite poursuivre l'exécution. La console devrait afficher les deux lignes :  
  
    ```cmd
    caught exception  
    goodbye  
    ```  
  
     mais elle n'affiche pas la ligne `here` .  
  
*  Une application de console c# fait référence à une bibliothèque de classes avec une classe qui possède deux méthodes, une méthode qui lève une exception et prend en charge et une deuxième méthode qui lève la même exception et ne gère pas :  
  
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
  
     Si **AccessViolationException** est cochée dans **Paramètres d'exception**, lorsque vous exécutez ce code dans le débogueur, l’exécution s’arrête à la ligne `throw` dans **ThrowHandledException()** et dans **ThrowUnhandledException()**.  
  
 Si vous souhaitez rétablir les paramètres d'exceptions par défaut, vous pouvez cliquer sur le bouton **Restaurer** de la barre d'outils :  
  
 ![Restaurer les valeurs par défaut dans les paramètres d’Exception](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
##  <a name="BKMK_UserUnhandled"></a> Demander au débogueur de continuer en cas d’exceptions non gérées par l’utilisateur  
 Si vous déboguez du code .NET ou JavaScript avec [Just My Code](../debugger/just-my-code.md), vous pouvez demander au débogueur de ne pas s’arrêter sur les exceptions qui ne sont pas gérées dans le code utilisateur, mais qui sont gérées ailleurs.  
  
1.  Dans la fenêtre **Paramètres d'exception** , ouvrez le menu contextuel en cliquant avec le bouton droit dans la fenêtre, puis en sélectionnant **Afficher les colonnes**. (Si vous avez désactivé **Uniquement mon code**, cette commande n'est pas visible.)  
  
2.  Vous devez normalement voir une deuxième colonne nommée **Actions supplémentaires**. Cette colonne affiche **Continuer en cas d'exception non gérée dans le code utilisateur** sur des exceptions spécifiques, ce qui signifie que le débogueur ne s'arrête pas si cette exception n'est pas gérée dans le code utilisateur alors qu'elle est gérée dans le code externe.  
  
3.  Vous pouvez modifier ce paramètre pour une exception particulière (en sélectionnant l'exception, en cliquant avec le bouton droit, puis en sélectionnant/désélectionnant **Continuer en cas d'exception non gérée dans le code utilisateur**) ou pour une catégorie entière d'exceptions (par exemple, toutes les exceptions Common Language Runtime).  
  
 Par exemple, les applications web ASP.NET gèrent les exceptions en les convertissant en code d’état HTTP 500 ([Gestion des exceptions dans l’API ASP.NET](http://www.asp.net/web-api/overview/error-handling/exception-handling)), ce qui peut compliquer l’identification de la source de l’exception. Dans l'exemple ci-dessous, le code utilisateur appelle `String.Format()` qui lève une exception <xref:System.FormatException>. L'exécution s'interrompt de la façon suivante :  
  
 ![s’arrête sur utilisateur&#45;exception gérée par](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
## <a name="add-and-delete-exceptions"></a>Ajouter et supprimer des exceptions  
 Vous pouvez ajouter et supprimer des exceptions. Vous pouvez supprimer n'importe quel type d'exception de n'importe quelle catégorie en sélectionnant l'exception et en cliquant sur le bouton **Supprimer** (signe moins) de la barre d'outils **Paramètres d'exception** , ou en cliquant avec le bouton droit sur l'exception et en sélectionnant **Supprimer** dans le menu contextuel. La suppression d'une exception a le même effet que si l'exception est désactivée, c'est-à-dire que le débogueur ne s'arrête pas lorsqu'elle est levée.  
  
 Pour ajouter une exception : dans la fenêtre **Paramètres d'exception** , sélectionnez l'une des catégories d'exception (par exemple, **Common Language Runtime**), puis cliquez sur le bouton **Ajouter** . Entrez le nom de l'exception (par exemple, **System.UriTemplateMatchException**). L'exception est ajoutée à la liste (par ordre alphabétique) et est automatiquement activée.  
  
 Si vous voulez ajouter une exception aux catégories Exceptions d'accès mémoire GPU, Exceptions du runtime JavaScript ou Exceptions Win32, vous devez inclure le code d'erreur, ainsi que la description.  
  
> [!TIP]
>  Vérifiez l'orthographe. Le **paramètres d’Exception** fenêtre ne vérifie pas l’existence d’une exception ajoutée. Par conséquent, si vous tapez **Sytem.UriTemplateMatchException**, vous obtenez une entrée pour cette exception (et non pour **System.UriTemplateMatchException**).  
  
 Paramètres d’exception sont conservés dans le fichier .suo de la solution, et s’appliquent à une solution spécifique. Vous ne pouvez pas réutiliser les paramètres d’exception spécifique sur les solutions. À ce stade, seules les exceptions ajoutées sont conservées ; les exceptions supprimées ne le sont pas. En d'autres termes, si vous ajoutez une exception, que vous fermez la solution, puis que vous la rouvrez, l'exception sera toujours présente. Mais si vous supprimez une exception et que vous fermez/rouvrez la solution, l'exception ne s'affiche plus.  
  
 La fenêtre **Paramètres d'exception** prend en charge les types d'exceptions génériques en C#, mais pas en Visual Basic. Pour effectuer un arrêt sur des exceptions telles que `MyNamespace.GenericException<T>`, vous devez ajouter l'exception en tant que **MyNamespace.GenericException'1**. Autrement dit, si vous avez créé une exception telle que celle-ci :  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Vous pouvez ajouter l'exception à **Paramètres d'exception** comme suit :  
  
 ![Ajout d’une exception générique](../debugger/media/addgenericexception.png "AddGenericException")  

## <a name="add-conditions-to-an-exception"></a>Ajouter des conditions à une exception

Vous pouvez définir des conditions sur les exceptions dans le **paramètres d’Exception** boîte de dialogue. Conditions actuellement pris en charge incluent les noms de module à inclure ou exclure de l’exception. En définissant des noms de module en tant que conditions, vous pouvez choisir Arrêter l’exécution de l’exception uniquement sur les modules de code particulier, ou vous pouvez éviter l’arrêt sur les modules particuliers.

> [!NOTE]
> Ajout de conditions à une exception est une nouveauté dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Pour ajouter des exceptions conditionnelles, choisissez la **modifier la condition** icône dans la boîte de dialogue Paramètres d’Exception ou avec le bouton droit de l’exception et sélectionnez **modifier les Conditions**.

![Conditions d’une Exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")
  
## <a name="see-also"></a>Voir aussi  
 [Poursuivre l’exécution après une Exception](../debugger/continuing-execution-after-an-exception.md)   
 [Comment : examiner du Code système après une Exception](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Comment : utiliser des contrôles d’exécution natifs](../debugger/how-to-use-native-run-time-checks.md)   
 [Utilisation d’exécution des vérifications sans la bibliothèque Runtime C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)
