---
title: Afficher les événements avec IntelliTrace | Microsoft Docs
description: Découvrez comment utiliser IntelliTrace dans Visual Studio Enterprise pour collecter des données sur des événements spécifiques, des catégories d’événements et des appels de fonction individuels.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8adaf62d7a9995bb5219d340e0e9a9999055c7a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884076"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Afficher les événements avec IntelliTrace en Visual Studio Enterprise (C#, Visual Basic)

Vous pouvez utiliser IntelliTrace pour collecter des informations sur des événements spécifiques ou des catégories d'événements, ou sur des appels de fonction individuels en plus d'événements. Les procédures suivantes montrent comment procéder.

Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition, mais pas dans les éditions Professional ou Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Configurer IntelliTrace

Vous pouvez essayer de déboguer avec seulement les événements IntelliTrace. Les événements IntelliTrace sont des événements de débogueur, des exceptions, des événements .NET Framework et d'autres événements système. Avant de commencer le débogage, vous devez activer ou désactiver des événements spécifiques pour contrôler les événements qu'IntelliTrace enregistre. Pour plus d’informations, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).

- Activez l'événement IntelliTrace pour l'accès aux fichiers. Accédez à la page **outils > Options > intellitrace > des événements IntelliTrace** , puis développez la catégorie **fichier** . Cochez la catégorie d'événements **Fichier** . Ainsi, tous les événements concernant les fichiers (accès, fermeture, suppression) sont cochés.

## <a name="create-your-app"></a>Créer votre application

1. Créez une application console C#. Ouvrez le fichier Program.cs et ajoutez l'instruction `using` suivante :

    ```csharp
    using System.IO;
    ```

2. Créez un <xref:System.IO.FileStream> dans la méthode Main, lisez dans ce flux, fermez-le et supprimez le fichier. Ajoutez une autre ligne juste pour avoir un emplacement où définir un point d'arrêt :

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Définissez un point d'arrêt sur `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Démarrer le débogage et afficher les événements IntelliTrace

1. Démarrez le débogage selon la procédure habituelle. (Appuyez sur **F5** ou cliquez sur **déboguer > démarrer le débogage**.)

    > [!TIP]
    > Gardez les fenêtres **variables locales** et **automatique** ouvertes pendant que vous déboguez pour voir et enregistrer les valeurs dans ces fenêtres.

2. L’exécution s’interrompt au point d’arrêt. Si vous ne voyez pas la fenêtre de **outils de diagnostic** , cliquez sur **déboguer > des événements IntelliTrace Windows >**.

    Dans la fenêtre **Outils de diagnostic** , recherchez l'onglet **Événements** (vous voyez normalement trois onglets, **Événements**, **Utilisation de la mémoire** et **Utilisation de l'UC**). L'onglet **Événements** affiche une liste chronologique des événements, qui se termine par le dernier événement avant que le débogueur ait interrompu l'exécution. Vous devez voir un événement nommé **Accès à WordSearchInputs.txt**.

    La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.

    ![Capture d’écran de la fenêtre de Visual Studio code. L’exécution est arrêtée à un point d’arrêt et l’onglet événements de la fenêtre Outils de diagnostic répertorie les événements.](../debugger/media/intellitrace-update1.png)

3. Sélectionnez l'événement pour développer ses détails.

    La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.

    ![Capture d’écran de l’onglet événements dans la fenêtre Visual Studio Outils de diagnostic. Un événement est sélectionné et développé pour afficher ses détails.](../debugger/media/intellitraceupdate1-singleevent.png)

    Vous pouvez choisir le lien de chemin d'accès pour ouvrir le fichier. Si le chemin d'accès complet n'est pas disponible, la boîte de dialogue **Ouvrir un fichier** s'affiche.

    Cliquez sur **activer le débogage d’historique**, qui définit le contexte du débogueur au moment où l’événement sélectionné a été collecté, en indiquant les données d’historique dans la pile des **appels**, les **variables locales** et les autres fenêtres du débogueur participant. Si le code source est disponible, Visual Studio déplace le pointeur jusqu'au code correspondant dans la fenêtre source afin de vous permettre de l'examiner.

    La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.

    ![Capture d’écran de la fenêtre de Visual Studio code. L’exécution est arrêtée à un point d’arrêt, un événement est sélectionné et la ligne de code correspondante est mise en surbrillance.](../debugger/media/historicaldebugging-update1.png)

4. Si vous ne trouvez pas le bogue, essayez de tester d'autres événements aboutissant au bogue. IntelliTrace peut également enregistrer des informations sur les appels pour vous permettre de parcourir pas à pas les appels de fonction.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez utiliser certaines des fonctionnalités avancées d’IntelliTrace avec le débogage d’historique :

- Pour afficher les instantanés, consultez [inspecter les États d’application précédents à l’aide d’IntelliTrace](../debugger/view-historical-application-state.md)
- Pour savoir comment inspecter des variables et parcourir le code, consultez [inspecter votre application avec le débogage d’historique](../debugger/historical-debugging-inspect-app.md)
