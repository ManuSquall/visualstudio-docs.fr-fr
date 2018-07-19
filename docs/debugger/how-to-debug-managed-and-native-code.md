---
title: 'Didacticiel : Déboguer du code managé et natif (mode mixte)'
description: Découvrez comment déboguer une DLL native à partir d’une application .NET Core ou .NET Framework à l’aide du débogage en mode mixte
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1f34f6af0a98e71f5feb910f84e8d67ada051ae9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057035"
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Didacticiel : Déboguer du code managé et natif dans Visual Studio

Visual Studio vous permet d’activer plusieurs types de débogueur lors du débogage, qui est appelée débogage en mode mixte. Dans ce didacticiel, vous définissez des options pour déboguer le code managé et natif dans une seule session de débogage. Ce didacticiel montre comment déboguer le code natif à partir d’une application gérée, mais vous pouvez également effectuer l’opération inverse, et [déboguer du code managé à partir d’une application native](../debugger/how-to-debug-in-mixed-mode.md). Le débogueur prend également en charge les autres types de débogage en mode mixte, telles que le débogage [code Python et natif](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) et à l’aide du débogueur de script dans types d’applications comme ASP.NET.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Créer une DLL native simple
> * Créer une simple application .NET Core ou .NET Framework pour appeler la DLL
> * Démarrez le débogueur
> * Atteindre un point d’arrêt dans l’application gérée
> * Pas à pas détaillé du code natif

## <a name="prerequisites"></a>Prérequis

* Vous devez avoir installé Visual Studio et le **développement Desktop en C++** charge de travail.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

    Si vous devez installer la charge de travail mais que vous avez déjà Visual Studio, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

* Vous devez également avoir le **développement .NET desktop** charge de travail ou le **.NET Core, le développement multiplateforme** charge de travail, selon le type d’application qui vous souhaitez créer.

## <a name="create-a-simple-native-dll"></a>Créer une DLL native simple

1. Dans Visual Studio, choisissez **fichier** > **New** > **projet**.

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C++**, **général** à partir de la section Modèles installés, puis, dans le volet du milieu sélectionnez **projet vide** .

1. Dans le **nom** , tapez **Mixed-débogage en Mode** et cliquez sur **OK**.

    Visual Studio crée le projet vide, ce qui s’affiche dans l’Explorateur de solutions dans le volet droit.

1. Dans l’Explorateur de solutions, cliquez sur le **fichiers sources** nœud dans le C++ de projet, puis choisissez **ajouter** > **un nouvel élément**, puis sélectionnez **C++ fichier (.cpp)**. Nommez le fichier **Mixed-Mode.cpp**, puis choisissez **ajouter**.

    Visual Studio ajoute le nouveau fichier C++.

1. Copiez le code suivant dans *Mixed-Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Dans l’Explorateur de solutions, cliquez sur le **fichiers d’en-tête** nœud dans le C++ de projet, puis choisissez **ajouter** > **un nouvel élément**, puis sélectionnez  **Fichier d’en-tête (.h)**. Nommez le fichier **Mixed-Mode.h**, puis choisissez **ajouter**.

    Visual Studio ajoute le nouveau fichier d’en-tête.

1. Copiez le code suivant dans *Mixed-Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Dans la barre d’outils de débogage, sélectionnez un **déboguer** configuration et **Any CPU** comme plateforme, ou, pour .NET Core, sélectionnez **x64** comme plateforme.

    > [!NOTE]
    > Dans .NET Core, choisissez **x64** comme plateforme. .NET core s’exécute toujours en mode 64 bits c’est nécessaire.

1. Dans l’Explorateur de solutions, cliquez sur le nœud du projet (**Mixed-débogage en Mode**) et choisissez **propriétés**.

1. Dans le **propriétés** page, choisissez **propriétés de Configuration** > **l’éditeur de liens** > **avancé**, et Ensuite, dans le **aucun Point d’entrée** liste déroulante, sélectionnez **non**. Appliquez des paramètres.

1. Dans le **propriétés** page, choisissez **propriétés de Configuration** > **général**, puis sélectionnez **bibliothèque dynamique (.dll)** à partir de la **Configuration Type** champ. Appliquez des paramètres.

    ![Basculer vers une DLL native](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Cliquez sur le projet et choisissez **déboguer** > **Build**.

    Le projet doit se générer sans erreurs.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Créer une application .NET Framework ou .NET Core simple pour appeler la DLL

1. Dans Visual Studio, choisissez **fichier** > **New** > **projet**.

1. Choisir un modèle pour votre code d’application.

    Pour .NET Framework, dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#**, **Windows Desktop** à partir de la section Modèles installés, puis, dans le panneau central, sélectionnez  **Application console (.NET Framework)**.

    Pour .NET Core, dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#**, **.NET Core** à partir de la section Modèles installés, puis, dans le volet du milieu sélectionnez  **Console App (.NET Core)**.

1. Dans le **nom** , tapez **Mixed_Mode_Calling_App** et cliquez sur **OK**.

    Visual Studio crée le projet de console, qui apparaît dans l’Explorateur de solutions dans le volet droit.

1. Dans *Program.cs*, remplacez le code par défaut par le code suivant :

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>Configurer le mode mixte de débogage (.NET Framework)

1. Dans l’Explorateur de solutions, cliquez sur managé **Mixed_Mode_Calling_App** de projet et choisissez **définir comme projet de démarrage**.

1. Avec le bouton droit managé **Mixed_Mode_Calling_App** de projet, puis choisissez **propriétés**, puis choisissez **déboguer** dans le volet gauche. Sélectionnez **activer le débogage du code natif**, puis fermez la page de propriétés pour enregistrer les modifications.

    ![Activer le débogage en mode mixte](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Configurer le mode mixte de débogage (.NET Core)

Dans la plupart des versions de Visual Studio 2017, vous devez activer le débogage en mode mixte pour le code natif dans une application .NET Core à l’aide du *launchSettings.json* de fichiers au lieu du **propriétés** page. Pour effectuer le suivi des mises à jour de l’interface utilisateur pour cette fonctionnalité, consultez ce [problème GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Ouvrez le *launchSettings.json* de fichiers dans le *propriétés* dossier. Par défaut, vous trouverez le fichier à cet emplacement.

    *C:\Users\<nom d’utilisateur > \source\repos\Mixed_Mode_Calling_App\Properties*

    Si le fichier n’est pas présent, ouvrez les propriétés du projet (avec le bouton droit managé **Mixed_Mode_Calling_App** projet dans l’Explorateur de solutions, puis sélectionnez **propriétés**). Apportez une modification temporaire dans le **déboguer** onglet et générez votre projet. Annuler la modification que vous avez apportées.

1. Dans le *lauchsettings.json* , ajoutez la propriété suivante :

    ```csharp
    "nativeDebugging": true
    ```

    Par conséquent, par exemple, votre fichier peut se présenter comme suit :

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définissez un point d’arrêt et démarrez le débogueur

1. Dans le projet c#, ouvrez *Program.cs* et définissez un point d’arrêt dans la ligne de code suivante en cliquant dans la marge de gauche :

    ```csharp
    int result = Multiply(7, 7);
    ```

    Un cercle rouge apparaît dans la marge de gauche pour indiquer que vous avez défini le point d’arrêt.

1. Appuyez sur **F5** (**déboguer** > **démarrer le débogage**) pour démarrer le débogueur.

    Le débogueur s’arrête sur le point d’arrêt que vous définissez. Une flèche jaune indique où le débogueur est actuellement suspendu.

## <a name="step-into-native-code"></a>Pas à pas détaillé du code natif

1. Pendant la suspension de l’application gérée, appuyez sur **F11** (**déboguer** > **pas à pas détaillé**).

    Le fichier d’en-tête avec le code natif s’ouvre et vous voyez la flèche jaune, où le débogueur est suspendu.

    ![Pas à pas détaillé du code natif](../debugger/media/mixed-mode-step-into-native-code.png)

    Maintenant, vous pouvez effectuer des opérations comme ensemble et points d’arrêt et inspecter les variables.

1. Pointez sur les variables pour voir leur valeur.

1. Examinez le **automatique** et **variables locales** windows pour afficher une variable et leurs valeurs.

    Pendant la suspension dans le débogueur, vous pouvez utiliser d’autres fonctionnalités du débogueur comme le **espion** fenêtre et la **pile des appels** fenêtre.

1. Appuyez sur **F11** à nouveau pour la débogueur une ligne d’avance.

1. Appuyez sur **MAJ + F11** (**déboguer** > **pas à pas sortant**) pour continuer l’exécution d’application et de suspendre à nouveau dans l’application gérée.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

    Félicitations ! Vous avez terminé le didacticiel sur le débogage en mode mixte.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à déboguer le code natif à partir d’une application gérée en activant le débogage en mode mixte. Pour une vue d’ensemble des autres fonctionnalités du débogueur, consultez l’article suivant :

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)
