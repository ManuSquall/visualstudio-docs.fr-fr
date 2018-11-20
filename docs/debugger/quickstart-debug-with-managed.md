---
title: Déboguer du code managé | Microsoft Docs
description: Déboguer du code C# ou Visual Basic à l’aide du débogueur Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637521"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Démarrage rapide : Déboguer du code managé à l’aide du débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C#** ou **Visual Basic**, choisissez **.NET Core** puis, dans le volet central, choisissez **Application console (.NET Core)**.

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop** et **.NET Core**, puis choisissez **Modifier**.

3. Tapez un nom comme **MyDbgApp**, puis cliquez sur **OK**.

    Visual Studio crée le projet.

4. Dans *Program.cs* ou *Module1.vb*, remplacez le code suivant

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    par le code suivant :

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > En Visual Basic, vérifiez que l’objet de démarrage est défini sur `Sub Main` (**Propriétés > Applications > Objet de démarrage**).

## <a name="set-a-breakpoint"></a>Définir un point d’arrêt

Un *point d’arrêt* est un marqueur qui indique où Visual Studio doit interrompre l’exécution du code pour vous permettre d’examiner les valeurs des variables ou le comportement de la mémoire, ou de voir si une branche de code est, ou non, exécutée. C’est la fonctionnalité la plus élémentaire du débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de l’appel de la fonction `doWork` (ou sélectionnez la ligne de code et appuyez sur **F9**).

    ![Définir un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Définir un point d’arrêt")

2. Appuyez maintenant sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Atteindre un point d’arrêt")

    Le débogueur se met en pause là où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et de l’application est en pause est indiquée par la flèche jaune. La ligne avec l’appel de la fonction `doWork` n’a pas encore été exécutée.

    > [!TIP]
    > Si vous avez défini un point d’arrêt dans une boucle ou une récurrence, ou si vous effectuez fréquemment un pas à pas dans du code contenant un grand nombre de points d’arrêt, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour mettre en pause votre code SEULEMENT quand certaines conditions sont remplies. Un point d’arrêt conditionnel peut faire gagner du temps et peut également faciliter le débogage de problèmes qui sont difficiles à reproduire.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe différentes commandes pour indiquer au débogueur de continuer. Nous montrons une commande de navigation pratique dans le code qui est une nouveauté de Visual Studio 2017.

Avec l’exécution en pause au point d’arrêt, placez le curseur sur l’instruction `c1.AddLast(20)` jusqu’à ce que le bouton vert **Exécuter jusqu’au clic** ![Exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaisse, puis appuyez sur le bouton **Exécuter jusqu’au clic**.

![Exécuter jusqu’au clic](../debugger/media/dbg-qs-run-to-click-csharp.png "Exécuter jusqu’au clic")

L’application poursuit son exécution en appelant `doWork`, puis s’arrête à la ligne de code où vous avez cliqué sur le bouton.

**F10** et **F11** sont des commandes clavier fréquemment utilisées pour avancer pas à pas dans le code. Pour obtenir des instructions plus détaillées, consultez le [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans une bulle d’informations (datatip)

1. Dans la ligne de code active (indiquée par le pointeur d’exécution jaune), placez le curseur de la souris sur l’objet `c1` pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip-csharp.png "Afficher un datatip")

    Le datatip vous montre la valeur actuelle de la variable `c1` et vous permet d’inspecter ses propriétés. Lors du débogage, si vous remarquez une valeur que vous n’attendiez pas, vous avez probablement un bogue dans les lignes de code précédentes ou d’appel. 

2. Développez le datatip pour examiner les valeurs de propriétés actuelles de l’objet `c1`.

3. Si vous voulez épingler le datatip pour continuer à voir la valeur de `c1` pendant que vous exécutez du code, cliquez sur la petite icône d’épingle. (Vous pouvez déplacer le datatip épinglé vers un emplacement approprié.)

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez un changement que vous voulez tester dans votre code au milieu d’une session de débogage, vous pouvez également le faire.

1. Cliquez sur la deuxième instance de `c2.First.Value` et remplacez `c2.First.Value` par `c2.Last.Value`.

2. Appuyez plusieurs fois sur **F10** (ou **Déboguer > Pas à pas principal**) pour faire avancer le débogueur et pour exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Modifier & Continuer")

    **F10** fait avancer le débogueur d’une instruction à la fois, mais il effectue un pas à pas principal sur les fonctions au lieu d’un pas à pas détaillé (le code que vous ignorez s’exécute tout de même).

Pour plus d’informations sur l’utilisation de Modifier & Continuer et sur les limitations de cette fonctionnalité, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
