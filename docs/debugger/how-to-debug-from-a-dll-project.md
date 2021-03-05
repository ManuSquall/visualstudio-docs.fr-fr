---
title: Débogage à partir d’un projet DLL | Microsoft Docs
description: Vous pouvez démarrer le débogage d’un projet DLL à partir du projet lui-même, en spécifiant l’application appelante dans les propriétés du projet. Pour plus d’informations, voir cet article.
ms.custom: SEO-VS-2020
ms.date: 10/10/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f6063c5a0343951bb098c6937ce13dac7100d4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160432"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Comment : déboguer à partir d’un projet DLL dans Visual Studio (C#, C++, Visual Basic, F #)

L’une des façons de déboguer un projet DLL consiste à spécifier l’application appelante dans les propriétés du projet DLL. Vous pouvez ensuite démarrer le débogage à partir du projet DLL lui-même. Pour que cette méthode fonctionne, l’application doit appeler la même DLL dans le même emplacement que celui que vous configurez. Si l’application trouve et charge une autre version de la DLL, cette version ne contient pas vos points d’arrêt. Pour d’autres méthodes de débogage des dll, consultez [débogage de projets dll](../debugger/debugging-dll-projects.md).

Si votre application managée appelle une DLL native ou si votre application native appelle une DLL managée, vous pouvez déboguer la DLL et l’application appelante. Pour plus d’informations, consultez [Comment : déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).

Les projets DLL natifs et managés ont des paramètres différents pour spécifier des applications appelées.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Spécifier une application appelante dans un projet DLL natif

1. Sélectionnez le projet DLL C++ dans **Explorateur de solutions**. Sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Dans la boîte de dialogue **\<Project> pages de propriétés** , assurez-vous que le champ **configuration** en haut de la fenêtre a la valeur **Déboguer**.

1. Sélectionnez **Configuration Propriétés**  >  **débogage**.

1. Dans la liste **débogueur à lancer** , choisissez débogueur **Windows local** ou **débogueur Windows distant**.

1. Dans la zone commande ou **commande distante** , **Ajoutez le chemin** d’accès complet et le nom de fichier de l’application appelante, tel qu’un fichier *. exe* .

   ![Fenêtre Propriétés de débogage](../debugger/media/dbg-debugging-properties-dll.png "Fenêtre Propriétés de débogage")

1. Ajoutez les arguments nécessaires du programme à la zone **Arguments de la commande**.

1. Sélectionnez **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Spécifier une application appelante dans un projet DLL managé

1. Sélectionnez le projet C# ou Visual Basic DLL dans **Explorateur de solutions**. Sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Vérifiez que le champ **Configuration** en haut de la fenêtre est défini sur **Débogage**.

1. Sous **action de démarrage**:

   - Pour .NET Framework dll, sélectionnez **Démarrer le programme externe**, puis ajoutez le chemin d’accès complet et le nom de l’application appelante.

   - Vous avez le choix **entre démarrer le navigateur avec l’URL** et renseigner l’URL d’une application ASP.net locale.

   - Pour les dll .NET Core, la page des propriétés de **débogage** est différente. Sélectionnez **exécutable** dans la liste déroulante **lancer** , puis ajoutez le chemin d’accès complet et le nom de l’application appelante dans le champ **exécutable** .

1. Ajoutez les arguments de ligne de commande nécessaires dans le champ arguments de la **ligne de commande** ou arguments de l' **application** .

   ![Fenêtre Propriétés de débogage C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "Fenêtre Propriétés de débogage C#")

1. Utilisez **fichier**  >  **enregistrer les éléments sélectionnés** ou **CTRL** + **S** pour enregistrer les modifications.

## <a name="debug-from-the-dll-project"></a>Déboguer à partir du projet DLL

1. Définissez des points d’arrêt dans le projet DLL.

1. Cliquez avec le bouton droit sur le projet DLL et choisissez **définir comme projet de démarrage**.

1. Assurez-vous que le champ **Configuration des solutions** a la valeur **Déboguer**. Appuyez sur **F5**, cliquez sur la flèche verte de **démarrage** ou sélectionnez **Déboguer**  >  **Démarrer le débogage**.

Si le débogage n’atteint pas vos points d’arrêt, assurez-vous que la sortie de votre DLL (par défaut, le dossier *\<project> \Debug.* ) est l’emplacement appelé par l’application appelante.

## <a name="see-also"></a>Voir aussi
- [Débogage de projets DLL](../debugger/debugging-dll-projects.md)
- [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
