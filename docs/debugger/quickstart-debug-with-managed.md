---
title: "Déboguer avec du code managé à l’aide du débogueur Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 03/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 212da1e214e6157f3e072df6466436883eced8f6
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="debug-with-managed-code-using-the-visual-studio-debugger"></a>Déboguer avec du code managé à l’aide du débogueur Visual Studio

Le débogueur Visual Studio fournit de nombreuses fonctionnalités puissantes pour vous aider à déboguer vos applications. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base.

## <a name="create-a-new-project"></a>Créer un projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C#** ou **Visual Basic**, choisissez **.NET Core**, puis, dans le volet central, choisissez **l’application Console (.NET Core)**.

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez le **développement de bureau .NET** et **.NET Core** charge de travail, puis choisissez **modifier**.

3. Tapez un nom tel que **MyDbgApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

4. Dans Program.cs ou Module1.vb, remplacez le code suivant

    ```c#
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

    ```c#
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

A *point d’arrêt* est un marqueur qui indique où Visual Studio interrompt votre en cours d’exécution de code afin de vous pouvez examiner les valeurs des variables ou le comportement de la mémoire, ou s’il faut ou non une branche de code la bonne exécution. Il s’agit de la fonctionnalité de base dans le débogage.

1. Pour définir le point d’arrêt, cliquez dans la marge à gauche de la `doWork` l’appel de fonction (ou sélectionnez la ligne de code, puis appuyez sur **F9**).

    ![Définir un point d’arrêt](../debugger/media/dbg-qs-set-breakpoint-csharp.png "définir un point d’arrêt")

2. Appuyez sur **F5** (ou choisissez **Déboguer > Démarrer le débogage**).

    ![Atteindre un point d’arrêt](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "atteint un point d’arrêt")

    Les temps de pause débogueur où vous avez défini le point d’arrêt. L’instruction où l’exécution du débogueur et l’application est suspendue est indiquée par la flèche jaune. La ligne avec la `doWork` appel de fonction n’a pas encore été exécutée.

    > [!TIP]
    > Si vous disposez d’un point d’arrêt dans une boucle ou une récurrence ou si vous avez plusieurs points d’arrêt que vous fréquemment parcourez, utilisez un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) pour vous assurer que votre code est interrompu uniquement lorsque certaines conditions sont remplies. Un point d’arrêt conditionnel pouvez gagner du temps et elle peut également rendre plus facile à déboguer les problèmes difficiles à reproduire.

## <a name="navigate-code"></a>Naviguer dans le code

Il existe plusieurs commandes pour instruire le débogueur pour continuer. Nous affichons une commande de navigation de code utiles est une nouveauté de Visual Studio 2017.

Pendant la suspension à un point d’arrêt, placez le curseur sur l’instruction `c1.AddLast(20)` jusqu'à ce que le vert **exécuter cliquer sur** bouton ![exécuter. Cliquez ensuite sur](../debugger/media/dbg-tour-run-to-click.png "RunToClick") s’affiche, puis appuyez sur la **Exécuter cliquer sur** bouton.

![Cliquez sur exécuter](../debugger/media/dbg-qs-run-to-click-csharp.png "exécuter cliquer sur")

L’application poursuit son exécution, l’appel `doWork`et s’arrête à la ligne de code où vous avez cliqué sur le bouton.

Les commandes clavier courantes utilisées pour parcourir le code inclure **F10** et **F11**. Pour obtenir des instructions plus détaillées, consultez le [Guide du débutant](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspecter des variables dans un datatip

1. Dans la ligne actuelle de code (indiquée par le pointeur d’exécution jaune), pointez sur le `c1` objet avec la souris pour afficher un datatip.

    ![Afficher un datatip](../debugger/media/dbg-qs-data-tip-csharp.png "afficher un datatip")

    Le datatip vous indique la valeur actuelle de la `c1` variable et vous permet d’inspecter ses propriétés. Lors du débogage, si vous voyez une valeur que vous ne prévoyez pas, vous avez probablement un bogue dans les lignes précédentes ou d’appel de code. 

2. Développez le datatip pour examiner les valeurs de propriété actuelles de le `c1` objet.

3. Si vous souhaitez épingler un datatip afin que vous pouvez continuer à afficher la valeur de `c1` lors de l’exécution de code, cliquez sur l’icône d’épingle petit. (Vous pouvez déplacer le datatip épinglé à un emplacement pratique).

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

Si vous identifiez une modification que vous souhaitez tester dans votre code au milieu d’une session de débogage, vous pouvez le faire, trop.

1. Cliquez sur la deuxième instance de `c2.First.Value` et modifiez `c2.First.Value` à `c2.Last.Value`.

2. Appuyez sur **F10** (ou **Déboguer > pas à pas principal**) plusieurs fois pour faire avancer le débogueur et exécuter le code modifié.

    ![Modifier & Continuer](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Modifier & Continuer")

    **F10** avance la déclaration de débogueur une fois, mais les étapes sur les fonctions au lieu de pas à pas détaillé dans les (le code que vous passez toujours s’exécute).

Pour plus d’informations sur l’utilisation de modifier & Continuer et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et d’inspecter des variables. Vous souhaiterez plus haut niveau sur les fonctionnalités du débogueur, ainsi que des liens vers plus d’informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
