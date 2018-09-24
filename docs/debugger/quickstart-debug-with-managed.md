---
title: Déboguer du code managé | Microsoft Docs
description: Débogage c# ou Visual Basic à l’aide du débogueur Visual Studio
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637521"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Démarrage rapide : Déboguer avec du code managé à l’aide du débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C#** ou **Visual Basic**, choisissez **.NET Core**, puis, dans le volet central, choisissez **Application console (.NET Core)**.

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez le **développement .NET desktop** et **.NET Core** charge de travail, puis choisissez **modifier**.

3. Tapez un nom tel que **MyDbgApp** et cliquez sur **OK**.

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

Un *point d’arrêt* est un marqueur qui indique où Visual Studio doit s’interrompre votre en cours d’exécution de code afin que vous puissiez examiner les valeurs des variables, ou le comportement de la mémoire, ou s’il faut ou non une branche de code est bien exécutée. C’est la fonctionnalité élémentaire lors du débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de la `doWork` appel de fonction (ou sélectionnez la ligne de code et appuyez sur **F9**).

    ![Définissez un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint-csharp.png "définir un point d’arrêt")

2. Appuyez maintenant sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "atteint un point d’arrêt")

    Les temps de pause de débogueur où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et l’application est en pause est indiquée par la flèche jaune. La ligne avec la `doWork` appel de fonction n’a pas encore été exécutée.

    > [!TIP]
    > Si vous disposez d’un point d’arrêt dans une boucle ou une récursivité ou si vous avez de nombreux points d’arrêt que vous passez fréquemment via, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour vous assurer que votre code est interrompue uniquement lorsque certaines conditions sont remplies. Un point d’arrêt conditionnel peut gagner du temps et il peut également apporter de plus facile à déboguer les problèmes qui sont difficiles à reproduire.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe différentes commandes pour indiquer au débogueur de continuer. Nous montrons une commande de navigation de code utiles est une nouveauté de Visual Studio 2017.

Pendant la suspension sur le point d’arrêt, placez le curseur sur l’instruction `c1.AddLast(20)` jusqu'à ce que le vert **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") s’affiche, puis appuyez sur la **Exécuter jusqu’au clic** bouton.

![Exécuter jusqu’au clic](../debugger/media/dbg-qs-run-to-click-csharp.png "exécuter jusqu’au clic")

L’application poursuit son exécution, l’appel `doWork`et s’arrête à la ligne de code où vous avez cliqué sur le bouton.

Les commandes de clavier courantes utilisées pour parcourir le code inclure **F10** et **F11**. Pour plus d’instructions détaillées, consultez le [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans un datatip

1. Dans la ligne actuelle de code (indiquée par le pointeur d’exécution jaune), placez le curseur sur la `c1` objet avec la souris pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip-csharp.png "afficher un datatip")

    Le datatip vous indique la valeur actuelle de la `c1` variable et vous permet d’inspecter ses propriétés. Lors du débogage, si vous voyez une valeur que vous ne pensez pas, vous avez probablement un bogue dans les lignes précédentes ou d’appel de code. 

2. Développez le datatip pour examiner les valeurs de propriété actuelles de la `c1` objet.

3. Si vous souhaitez épingler un datatip afin que vous pouvez continuer à afficher la valeur de `c1` pendant que vous exécutez du code, cliquez sur l’icône d’épingle petit. (Vous pouvez déplacer le datatip épinglé à un emplacement unique et pratique).

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous souhaitez tester dans votre code au milieu d’une session de débogage, vous pouvez le faire, trop.

1. Cliquez sur la deuxième instance de `c2.First.Value` et modifiez `c2.First.Value` à `c2.Last.Value`.

2. Appuyez sur **F10** (ou **Déboguer > pas à pas principal**) plusieurs fois pour faire avancer le débogueur et exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Modifier & Continuer")

    **F10** avance l’instruction du débogueur une à une heure, mais les étapes sur les fonctions au lieu de pas à pas détaillé dans les (le code que vous ignorez encore s’exécute).

Pour plus d’informations sur l’utilisation de modifier et continuer et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et inspecter les variables. Voulez-vous obtenir une vue d’ensemble des fonctionnalités de débogueur ainsi que des liens vers d’autres informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
