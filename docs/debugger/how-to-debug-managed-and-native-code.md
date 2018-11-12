---
title: 'Didacticiel : Déboguer du code managé et natif (mode mixte)'
description: Découvrez comment déboguer une DLL native à partir d’une application .NET Core ou .NET Framework à l’aide du débogage en mode mixte
ms.custom: ''
ms.date: 11/02/2018
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
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295759"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Didacticiel : Déboguer du code managé et natif dans la même session de débogage

Visual Studio vous permet d’activer plusieurs types de débogueur dans une session de débogage, qui est appelée le débogage en mode mixte. Dans ce didacticiel, vous apprenez à déboguer le code managé et natif dans une seule session de débogage. 

Ce didacticiel montre comment déboguer le code natif à partir d’une application gérée, mais vous pouvez également [déboguer du code managé à partir d’une application native](../debugger/how-to-debug-in-mixed-mode.md). Le débogueur prend également en charge les autres types de débogage en mode mixte, telles que le débogage [code Python et natif](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)et à l’aide du débogueur de script dans types d’applications comme ASP.NET.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Créer une DLL native simple
> * Créer une simple application .NET Core ou .NET Framework pour appeler la DLL
> * Configurer le débogage en mode mixte
> * Démarrez le débogueur
> * Atteindre un point d’arrêt dans l’application gérée
> * Pas à pas détaillé du code natif

## <a name="prerequisites"></a>Prérequis

Vous devez disposer de Visual Studio est installé, les charges de travail suivantes :
- **Développement Desktop en C++**
- Soit **développement .NET desktop** ou **.NET Core, le développement multiplateforme**, selon le type d’application que vous souhaitez créer.

Si vous n’avez pas Visual Studio, accédez à la [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) page pour l’installer gratuitement.

Si vous avez installé Visual Studio, mais que vous n’avez pas les charges de travail que vous avez besoin, sélectionnez **ouvrir Visual Studio Installer** dans le volet gauche de Visual Studio **nouveau projet** boîte de dialogue. Dans le programme d’installation Visual Studio, sélectionnez les charges de travail vous avez besoin, puis sélectionnez **modifier**.

## <a name="create-a-simple-native-dll"></a>Créer une DLL native simple

**Pour créer les fichiers du projet de DLL :**

1. Dans Visual Studio, sélectionnez **fichier** > **New** > **projet**.

1. Dans le **nouveau projet** boîte de dialogue **Visual C++**, sélectionnez **autres**, puis sélectionnez **projet vide** dans le volet central.

1. Dans le **nom** , tapez **Mixed_Mode_Debugging**, puis sélectionnez **OK**.

   Visual Studio crée le projet vide et l’affiche dans **l’Explorateur de solutions**.

1. Dans **l’Explorateur de solutions**, sélectionnez **fichiers sources**, puis sélectionnez **projet** > **ajouter un nouvel élément**. Ou, avec le bouton droit **fichiers sources** et sélectionnez **ajouter** > **un nouvel élément**. 

1. Dans le **un nouvel élément** boîte de dialogue, sélectionnez **fichier C++ (.cpp)**. Type **Mixed_Mode.cpp** dans le **nom** champ, puis sélectionnez **ajouter**.

    Visual Studio ajoute le nouveau fichier C++ **l’Explorateur de solutions**.

1. Copiez le code suivant dans *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Dans **l’Explorateur de solutions**, sélectionnez **fichiers d’en-tête**, puis sélectionnez **projet** > **ajouter un nouvel élément**. Ou, avec le bouton droit **fichiers d’en-tête** et sélectionnez **ajouter** > **un nouvel élément**. 

1. Dans le **un nouvel élément** boîte de dialogue, sélectionnez **fichier d’en-tête (.h)**. Type **Mixed_Mode.h** dans le **nom** champ, puis sélectionnez **ajouter**.

   Visual Studio ajoute le nouveau fichier d’en-tête à **l’Explorateur de solutions**.

1. Copiez le code suivant dans *Mixed_Mode.h*:

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

1. Sélectionnez **fichier** > **Enregistrer tout** ou appuyez sur **Ctrl**+**MAJ**+**S**  pour enregistrer les fichiers.

**Pour configurer et générer le projet DLL :**

1. Dans la barre d’outils Visual Studio, sélectionnez **déboguer** configuration et **x86** ou **x64** plateforme. Si votre application appelante sera .NET Core, qui s’exécute toujours en mode 64 bits, sélectionnez **x64** comme plateforme.

1. Dans **l’Explorateur de solutions**, sélectionnez le **Mixed_Mode_Debugging** nœud de projet et sélectionnez le **propriétés** icône, ou cliquez sur le nœud de projet et sélectionnez **Propriétés**.

1. En haut de la **propriétés** volet, assurez-vous que le **Configuration** a la valeur **active (débogage)** et le **plateforme** est identique à ce que vous définir dans la barre d’outils : **x64**, ou **Win32** pour x86 plateforme. 

   > [!IMPORTANT]
   > Si vous basculez de plate-forme à partir de **x86** à **x64** ou vice versa, vous devez reconfigurer les propriétés de la nouvelle plate-forme. 

1. Sous **propriétés de Configuration** dans le volet gauche, sélectionnez **l’éditeur de liens** > **avancé**et dans la liste déroulante à côté **aucun Point d’entrée**, sélectionnez **non**. Si vous deviez le modifier pour **non**, sélectionnez **appliquer**.

1. Sous **propriétés de Configuration**, sélectionnez **général**et dans la liste déroulante à côté de **Configuration Type**, sélectionnez **bibliothèque dynamique (.dll)**. Sélectionnez **appliquer**, puis sélectionnez **OK**.

   ![Basculer vers une DLL native](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Sélectionnez le projet dans **l’Explorateur de solutions** , puis sélectionnez **Build** > **générer la Solution**, appuyez sur **F7**, ou avec le bouton droit le projet et sélectionnez **Build**.

   Le projet doit se générer sans erreurs.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Créer une application gérée simple pour appeler la DLL

1. Dans Visual Studio, choisissez **fichier** > **New** > **projet**.

   > [!NOTE]
   > Bien que vous pouvez également ajouter le nouveau projet géré à votre solution C++ existante, création d’une solution prend en charge plusieurs scénarios de débogage.

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#** et dans le volet central :

   - Pour une application .NET Framework, sélectionnez **application Console (.NET Framework)**.
   
   - Pour une application .NET Core, sélectionnez **application Console (.NET Core)**.

1. Dans le **nom** , tapez **Mixed_Mode_Calling_App**, puis sélectionnez **OK**.

   Visual Studio crée le projet vide et l’affiche dans **l’Explorateur de solutions**.

1. Remplacez tout le code dans *Program.cs* par le code suivant :

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
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
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

1. Dans le nouveau code, remplacez le chemin d’accès de fichier dans `[DllImport]` avec votre chemin d’accès à la *Mixed_Mode_Debugging.dll* vous venez de créer. Consultez le commentaire de code pour les indicateurs. Veillez à remplacer le *nom d’utilisateur* espace réservé.

1. Sélectionnez **fichier** > **enregistrer le fichier Program.cs** ou appuyez sur **Ctrl**+**S** pour enregistrer le fichier.

## <a name="configure-mixed-mode-debugging"></a>Configurer le débogage en mode mixte 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Pour configurer le débogage en mode mixte pour une application .NET Framework 

1. Dans **l’Explorateur de solutions**, sélectionnez le **Mixed_Mode_Calling_App** nœud de projet et sélectionnez le **propriétés** icône, ou cliquez sur le nœud de projet et sélectionnez **Propriétés**.

1. Sélectionnez **déboguer** dans le volet gauche, sélectionnez le **activer le débogage du code natif** case à cocher, puis fermez la page de propriétés pour enregistrer les modifications.

    ![Activer le débogage en mode mixte](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Pour configurer le débogage en mode mixte pour une application .NET Core 

Dans la plupart des versions de Visual Studio 2017, vous devez utiliser le *launchSettings.json* fichier au lieu de propriétés du projet pour activer le débogage en mode mixte pour le code natif dans une application .NET Core. Pour effectuer le suivi des mises à jour de l’interface utilisateur pour cette fonctionnalité, consultez ce [problème GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Dans **l’Explorateur de solutions**, développez **propriétés**, puis ouvrez le *launchSettings.json* fichier. 

   >[!NOTE]
   >Par défaut, *launchSettings.json* est dans *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Si *launchSettings.json* n’existe pas, sélectionnez le **Mixed_Mode_Calling_App** projet **l’Explorateur de solutions** , puis sélectionnez le **propriétés** icône, ou cliquez sur le projet et sélectionnez **propriétés**. Apportez une modification temporaire dans le **déboguer** onglet et générez le projet. Cela créera un *launchSettings.json* fichier. Annuler la modification que vous avez apportées dans le **déboguer** onglet.

1. Dans le *lauchsettings.json* , ajoutez la ligne suivante :

    ```csharp
    "nativeDebugging": true
    ```

    Le fichier complet ressemblera à l’exemple suivant :

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Définissez un point d’arrêt et démarrer le débogage

1. Dans le C# projet, ouvrez *Program.cs*. Définir un point d’arrêt sur la ligne de code suivante en cliquant dans la marge de gauche, sélectionnez la ligne et en appuyant sur **F9**, ou clic droit sur la ligne et en sélectionnant **point d’arrêt**  >  **Insérer le point d’arrêt**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Un cercle rouge apparaît dans la marge gauche où vous avez défini le point d’arrêt.

1. Appuyez sur **F5**, sélectionnez la flèche verte dans la barre d’outils de Visual Studio, ou **déboguer** > **démarrer le débogage** pour démarrer le débogage.

   Le débogueur s’arrête sur le point d’arrêt que vous définissez. Une flèche jaune indique où le débogueur est actuellement suspendu.

## <a name="step-in-and-out-of-native-code"></a>Étape et l’extraction du code natif

1. Pendant le débogage est en pause dans l’application gérée, appuyez sur **F11**, ou sélectionnez **déboguer** > **pas à pas détaillé**.

   Le *Mixed_Mode.h* fichier d’en-tête natif s’ouvre et vous voyez la flèche jaune, où le débogueur est suspendu.

   ![Pas à pas détaillé du code natif](../debugger/media/mixed-mode-step-into-native-code.png)

1. Maintenant, vous pouvez définir et atteindre des points d’arrêt et inspecter les variables dans le code natif ou managé.

   - Placez le curseur sur les variables dans le code source pour afficher leurs valeurs.

   - Examinez de variable et leurs valeurs dans le **automatique** et **variables locales** windows.

   - Pendant la suspension dans le débogueur, vous pouvez également utiliser le **espion** windows et le **pile des appels** fenêtre.

1. Appuyez sur **F11** à nouveau pour la débogueur une ligne d’avance.

1. Appuyez sur **MAJ**+**F11** ou sélectionnez **déboguer** > **pas à pas sortant** poursuivre l’exécution et s’arrête à nouveau dans le application gérée.

1. Appuyez sur **F5** ou sélectionnez la flèche verte pour continuer le débogage de l’application.

Félicitations ! Vous avez terminé le didacticiel sur le débogage en mode mixte.

## <a name="next-step"></a>Étape suivante

Dans ce didacticiel, vous avez appris à déboguer le code natif à partir d’une application gérée en activant le débogage en mode mixte. Pour une vue d’ensemble des autres fonctionnalités du débogueur, consultez :

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)
