---
title: Projets de Debug DLL (fr) Microsoft Docs
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302202"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debug DL Dans Visual Studio (C, CMD, Visual Basic, F)

Un DLL (bibliothèque à liaison dynamique) est une bibliothèque qui contient du code et des données qui peuvent être utilisées par plus d’une application. Vous pouvez utiliser Visual Studio pour créer, construire, configurer et déboiffer les DLL.

## <a name="create-a-dll"></a>Créer un DLL

Les modèles de projet Visual Studio suivants peuvent créer des DLL :

- Bibliothèque de classe C, Visual Basic ou F
- Bibliothèque de contrôle des formulaires Windows de base (WCF) (C) ou Visual Basic
- Bibliothèque dynamique-link (DLL)

Pour plus d’informations, voir [les techniques de débogage MFC](../debugger/mfc-debugging-techniques.md).

Déboguer une bibliothèque WCF est similaire à déboguer une bibliothèque de classe. Pour plus de détails, voir [Windows Forms Controls](/dotnet/framework/winforms/controls/index).

Vous appelez habituellement un DLL d’un autre projet. Lorsque vous déboiffez le projet d’appel, en fonction de la configuration DLL, vous pouvez entrer et déboiffer le code DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuration DLL de déboiffé

Lorsque vous utilisez un modèle de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visual Studio pour créer une application, créez automatiquement les paramètres requis pour les configurations de construction Debug et Release. Vous pouvez modifier ces paramètres si nécessaire. Pour plus d’informations, consultez les articles suivants :

- [Paramètres de projet pour une configuration de débogé de C](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour les configurations de débogé de C](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Comment : Définir de déboiffé et relâcher les configurations](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Définir CMD DebuggableAttribute

Pour que le débbuggeur se joint à un DLL C, le code CMD doit émettre `DebuggableAttribute`.

**Pour `DebuggableAttribute`définir :**

1. Sélectionnez le projet DLL de CMD dans **Solution Explorer** et sélectionnez l’icône **Propriétés,** ou cliquez à droite sur le projet et sélectionnez **les propriétés**.

1. Dans le volet **Propriétés,** sous **Linker** > **Debugging**, sélectionnez **Oui (/ASSEMBLYDEBUG)** pour **Debuggable Assembly**.

Pour plus d’informations, voir [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Définir les emplacements des fichiers DLL C/C

Pour déboiffer un DLL externe, un projet d’appel doit être en mesure de trouver le DLL, son [fichier .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), et tous les autres fichiers de la DLL nécessite. Vous pouvez créer une tâche de construction personnalisée pour copier ces fichiers à votre * \<dossier de projet>-Debug* dossier de sortie, ou vous pouvez copier les fichiers il manuellement.

Pour les projets C/CMD, vous pouvez définir les emplacements d’en-tête et de fichiers LIB dans les pages de propriété du projet, au lieu de les copier au dossier de sortie.

**Pour définir les emplacements d’en-tête et de fichiers LIB :**

1. Sélectionnez le projet DLL C/CMD dans **Solution Explorer** et sélectionnez l’icône **Propriétés,** ou cliquez à droite sur le projet et sélectionnez **les propriétés**.

1. En haut de la vitre **propriétés,** sous **Configuration**, sélectionnez **Toutes les configurations**.

1. Sous **C/C-General** > **General** > **Additional Include Directories**, spécifiez le dossier qui a des fichiers d’en-tête.

1. Sous **Linker** > **General** > Additional Libraries**Directories**, spécifiez le dossier qui a des fichiers LIB.

1. Sous **Linker** > **Input** > **Dépendances supplémentaires**, spécifiez le chemin complet et le nom de fichier pour les fichiers LIB.

1. Sélectionnez **OK**.

Pour plus d’informations sur les paramètres du projet C, consultez [la référence de la page de propriété Windows CMD](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Construire une version Debug

Assurez-vous de construire une version Debug de la DLL avant de commencer à débogage. Pour déboiffer un DLL, une application d’appel doit être en mesure de trouver son [fichier .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et tous les autres fichiers dont le DLL a besoin.

Vous pouvez créer une tâche de construction personnalisée pour copier les fichiers DLL à votre * \<dossier de projet d’appel>-Debug* dossier de sortie, ou vous pouvez copier les fichiers il manuellement.

Assurez-vous d’appeler le DLL à son emplacement correct. Cela peut sembler évident, mais si une application d’appel trouve et charge une copie différente de la DLL, le débbugger ne sera jamais frapper les points d’arrêt que vous définissez.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Debug un DLL

Vous ne pouvez pas exécuter un DLL directement. Il doit être appelé par une application, généralement un fichier *.exe.* Pour plus d’informations, voir [les projets Visual Studio - C .](/cpp/ide/creating-and-managing-visual-cpp-projects)

Pour déboguer un DLL, vous pouvez [commencer à déboguer à partir de l’application d’appel](#vxtskdebuggingdllprojectsthecallingapplication), ou [déboguer du projet DLL](how-to-debug-from-a-dll-project.md) en spécifiant son application d’appel. Vous pouvez également utiliser la [fenêtre](#vxtskdebuggingdllprojectstheimmediatewindow) immédiate de déboggeur pour évaluer les fonctions ou méthodes DLL au moment de la conception, sans utiliser une application d’appel.

Pour plus d’informations, voir [d’abord regardez le débbugger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Commencez à débogage à partir de l’application d’appel

L’application qui appelle un DLL peut être:

- Une application [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’un projet dans la même solution ou une solution différente de la DLL.
- Une application existante qui est déjà déployée et en cours d’exécution sur un ordinateur de test ou de production.
- Située sur le web et accessible via une URL.
- Une application web avec une page web qui intègre le DLL.

Pour déboiffer un DLL à partir d’une application d’appel, vous pouvez :

- Ouvrez le projet pour l’application d’appel, et commencez à débogage en sélectionnant **Debug** > **Start Debugging** ou en appuyant sur **F5**.

  or

- Attachez-vous à une application déjà déployée et en cours d’exécution sur un ordinateur de test ou de production. Utilisez cette méthode pour les DLL sur les sites Web ou dans les applications Web. Pour plus d’informations, voir [Comment : Attachez-vous à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Avant de commencer à déboguer l’application d’appel, définissez un point d’arrêt dans le DLL. Voir [à l’aide de points d’arrêt](../debugger/using-breakpoints.md). Lorsque le point d’arrêt DLL est atteint, vous pouvez passer à travers le code, en observant l’action à chaque ligne. Pour plus d’informations, voir [Code Naviguer dans le débbugger](../debugger/navigating-through-code-with-the-debugger.md).

Lors du débogage, vous pouvez utiliser la fenêtre **Modules** pour vérifier les DLL et *.exe* fichiers les charges de l’application. Pour ouvrir la fenêtre **Modules,** tout en débogage, sélectionnez**Modules****Windows** >  **Debug** > . Pour plus d’informations, voir [Comment : Utilisez la fenêtre Modules](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Utiliser la fenêtre immédiate

Vous pouvez utiliser la fenêtre **immédiate** pour évaluer les fonctions ou les méthodes DLL au moment de la conception. La fenêtre **immédiate** joue le rôle d’une application d’appel.

>[!NOTE]
>Vous pouvez utiliser la fenêtre **immédiate** au moment de la conception avec la plupart des types de projet. Il n’est pas pris en charge pour SQL, projets web, ou script.

Par exemple, pour tester `Test` une `Class1`méthode nommée en classe :

1. Avec l’ouverture du projet DLL, ouvrez la fenêtre **immédiate** en sélectionnant **Debug** > **Windows** > **Immediate** ou en appuyant sur **Ctrl**+**Alt**+**I**.

1. Instantanéssez un objet `Class1` de type en tapant le code C suivant dans la fenêtre **immédiate** et en appuyant **sur Enter**. Ce code géré fonctionne pour C et Visual Basic, avec des modifications syntaxiques appropriées :

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, tous les noms doivent être qualifiés complets. Toute méthode ou variable doit être dans la portée et le contexte actuels lorsque le service linguistique tente d’évaluer l’expression.

1. En supposant que `Test` nécessite un paramètre `int` , évaluez `Test` à l'aide de la fenêtre **Exécution** :

   ```csharp
   ?obj.Test(10);
   ```

   Le résultat s’imprime dans la fenêtre **immédiate.**

1. Vous pouvez continuer à déboguer `Test` en y insérant un point d’arrêt, puis en réévaluant la fonction.

   Le point d’arrêt sera touché, `Test`et vous pouvez passer à travers . Une fois que l’exécution a quitté `Test`, le débogueur repasse en mode Création.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Débogage en mode mixte

Vous pouvez écrire une application d’appel pour un DLL dans le code géré ou natif. Si votre application native appelle un DLL géré et que vous souhaitez déboiffer les deux, vous pouvez activer les débingiers gérés et natifs dans les propriétés du projet. Le processus exact dépend si vous voulez commencer à débogage du projet DLL ou le projet d’application d’appel. Pour plus d’informations, voir [Comment : Debug en mode mixte.](../debugger/how-to-debug-in-mixed-mode.md)

Vous pouvez également déboiffer un DLL natif d’un projet d’appel géré. Pour plus d’informations, voir [Comment déboiffer le code géré et natif](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Voir aussi
- [Déboguer du code managé](../debugger/debugging-managed-code.md)
- [Préparez-vous à déboiffer les projets de C](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour une configuration de débogé de C](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour les configurations de C Debug](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Visual Basic Debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
