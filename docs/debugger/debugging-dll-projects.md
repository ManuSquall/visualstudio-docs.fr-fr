---
title: Déboguer des projets DLL | Microsoft Docs
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
ms.openlocfilehash: c22da2a31be1389ca0b60df6cc64ac6c9155ad69
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102580"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Déboguer des DLL dans Visual Studio (C#, C++, Visual Basic, F#)

Une DLL (bibliothèque de liens dynamiques) est une bibliothèque qui contient le code et les données qui peuvent être utilisées par plusieurs applications. Vous pouvez utiliser Visual Studio pour créer, générer, configurer et déboguer des DLL.

## <a name="create-a-dll"></a>Créer une DLL

Les modèles de projet Visual Studio suivantes peuvent créer des DLL :

- C#, Visual Basic, ou F# bibliothèque de classes
- C#ou Visual Basic Windows Forms de bibliothèque de contrôles (WCF)
- Bibliothèque de liens C++ dynamiques (DLL)

Pour plus d’informations, consultez [Techniques de débogage de MFC](../debugger/mfc-debugging-techniques.md).

Débogage d’une bibliothèque de WCF est semblable au débogage d’une bibliothèque de classes. Pour plus d’informations, consultez [des contrôles Windows Forms](/dotnet/framework/winforms/controls/index).

Généralement, vous appelez une DLL à partir d’un autre projet. Lorsque vous déboguez le projet appelant, selon la configuration de la DLL, vous pouvez le pas à pas détaillé et déboguer le code de la DLL.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configuration de débogage DLL

Lorsque vous utilisez un modèle de projet Visual Studio pour créer une application, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations de build Debug et Release. Vous pouvez modifier ces paramètres si nécessaire. Pour plus d’informations, consultez les articles suivants :

- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Définir l’attribut DebuggableAttribute C++

Pour que le débogueur s’attache à une DLL C++, le code C++ doit émettre `DebuggableAttribute`.

**Pour définir `DebuggableAttribute`:**

1. Sélectionnez le projet de DLL C++ dans **l’Explorateur de solutions** et sélectionnez le **propriétés** icône, ou cliquez sur le projet et sélectionnez **propriétés**.

1. Dans le **propriétés** volet, sous **l’éditeur de liens** > **débogage**, sélectionnez **Oui (/ ASSEMBLYDEBUG)** pour  **Assembly pouvant être débogué**.

Pour plus d’informations, consultez [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a> Définir les emplacements des fichiers DLL C/C++

Pour déboguer une DLL externe, un projet appelant doit être en mesure de trouver la DLL, son [fichier .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)et tout autre fichier requiert la DLL. Vous pouvez créer une tâche de génération personnalisée pour copier ces fichiers à votre  *\<dossier du projet > \Debug* dossier de sortie, ou vous pouvez copier les fichiers manuellement.

Pour les projets C/C++, vous pouvez définir des en-tête et les emplacements des fichiers LIB dans les pages de propriétés de projet, au lieu de les copier dans le dossier de sortie.

**Pour définir le C/C++ en-tête et LIB emplacements de fichiers :**

1. Sélectionnez le projet de DLL C/C++ dans **l’Explorateur de solutions** et sélectionnez le **propriétés** icône, ou cliquez sur le projet et sélectionnez **propriétés**.

1. En haut de la **propriétés** volet, sous **Configuration**, sélectionnez **toutes les Configurations**.

1. Sous **C/C++** > **général** > **autres répertoires Include**, spécifiez le dossier contenant les fichiers d’en-tête.

1. Sous **l’éditeur de liens** > **général** > **répertoires de bibliothèques supplémentaires**, spécifiez le dossier qui comporte les fichiers LIB.

1. Sous **l’éditeur de liens** > **entrée** > **dépendances supplémentaires**, spécifiez le chemin d’accès complet et le nom de fichier pour les fichiers LIB.

1. Sélectionnez **OK**.

Pour plus d’informations sur les paramètres de projet C++, consultez [pages de propriétés (Visual C++)](/cpp/ide/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Créer une version Debug

Veillez à générer une version Debug de la DLL avant de commencer le débogage. Pour déboguer une DLL, une application appelante doit être en mesure de trouver son [fichier .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et tout autre fichier requiert la DLL.

Vous pouvez créer une tâche de génération personnalisée pour copier les fichiers DLL à votre  *\<appelant le dossier du projet > \Debug* dossier de sortie, ou vous pouvez copier les fichiers manuellement.

Veillez à appeler la DLL à son emplacement approprié. Cela peut sembler évident, mais si une application appelante détecte et charge une autre copie de la DLL, le débogueur n’atteindra jamais les points d’arrêt que vous définissez.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Déboguer une DLL

Vous ne pouvez pas exécuter une DLL directement. Il doit être appelé par une application, généralement un *.exe* fichier. Pour plus d’informations, consultez [créer et gérer des projets Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Pour déboguer une DLL, vous pouvez [démarrer le débogage à partir de l’application appelante](#vxtskdebuggingdllprojectsthecallingapplication), ou [déboguer à partir du projet DLL](how-to-debug-from-a-dll-project.md) en spécifiant son application appelante. Vous pouvez également utiliser le débogueur [fenêtre exécution](#vxtskdebuggingdllprojectstheimmediatewindow) pour évaluer des méthodes ou des fonctions DLL au moment du design, sans utiliser une application appelante.

Pour plus d’informations, consultez [tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Démarrer le débogage à partir de l’application appelante

L’application qui appelle une DLL peut être :

- Une application à partir d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet dans le même ou une autre solution à partir de la DLL.
- Une application existante qui est déjà déployée et une en cours d’exécution sur un ordinateur de test ou de production.
- Située sur le web et accessible via une URL.
- Une application web avec une page web qui incorpore la DLL.

Pour déboguer une DLL à partir d’une application appelante, vous pouvez :

- Ouvrez le projet pour l’application appelante et démarrez le débogage en sélectionnant **déboguer** > **démarrer le débogage** ou en appuyant sur **F5**.

  ou

- Attacher à une application qui est déjà déployé et en cours d’exécution sur un ordinateur de test ou de production. Utilisez cette méthode pour les DLL sur les sites Web ou dans les applications web. Pour plus d'informations, voir [Procédure : Attacher à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Avant de commencer le débogage de l’application appelante, définissez un point d’arrêt dans la DLL. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md). Lorsque le point d’arrêt de la DLL est atteint, vous pouvez parcourir le code, en observant l’action à chaque ligne. Pour plus d’informations, consultez [parcourir le code dans le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

Pendant le débogage, vous pouvez utiliser la **Modules** fenêtre pour vérifier les DLL et *.exe* fichiers le chargement de l’application. Pour ouvrir le **Modules** fenêtre, pendant le débogage, sélectionnez **déboguer** > **Windows** > **Modules**. Pour plus d'informations, voir [Procédure : Utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Utiliser la fenêtre exécution

Vous pouvez utiliser la **immédiat** fenêtre pour évaluer des méthodes ou des fonctions DLL au moment du design. Le **immédiat** fenêtre joue le rôle d’une application appelante.

>[!NOTE]
>Vous pouvez utiliser la **immédiat** fenêtre au moment du design avec la plupart des types de projets. Il n’est pas pris en charge pour SQL, projets web ou un script.

Par exemple, pour tester une méthode nommée `Test` dans la classe `Class1`:

1. Le projet DLL ouvert, ouvrez le **immédiat** en sélectionnant **déboguer** > **Windows** > **immédiat**ou en appuyant sur **Ctrl**+**Alt**+**je**.

1. Instancier un objet de type `Class1` en tapant la commande suivante C# de code dans le **immédiat** fenêtre et en appuyant sur **entrée**. Ce code managé fonctionne pour C# et Visual Basic, avec les modifications de syntaxe appropriées :

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, tous les noms doivent être qualifiés complets. Les méthodes ou les variables doivent être dans l’étendue actuelle et le contexte lorsque le service de langage essaie d’évaluer l’expression.

1. En supposant que `Test` nécessite un paramètre `int` , évaluez `Test` à l'aide de la fenêtre **Exécution** :

   ```csharp
   ?obj.Test(10);
   ```

   Le résultat imprime dans le **immédiat** fenêtre.

1. Vous pouvez continuer à déboguer `Test` en y insérant un point d’arrêt, puis en réévaluant la fonction.

   Le point d’arrêt est atteint, et vous pouvez parcourir `Test`. Une fois que l’exécution a quitté `Test`, le débogueur repasse en mode Création.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Débogage en mode mixte

Vous pouvez écrire une application appelante pour une DLL en code managé ou natif. Si votre application native appelle une DLL managée et que vous souhaitez déboguer les deux, vous pouvez activer les débogueurs managés et natifs dans les propriétés du projet. Le processus exact varie selon que vous souhaitez démarrer le débogage à partir du projet de DLL ou le projet d’application appelant. Pour plus d'informations, voir [Procédure : Déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).

Vous pouvez également déboguer une DLL native à partir d’un projet appelant managé. Pour plus d’informations, consultez [comment déboguer le code managé et natif](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Voir aussi
- [Déboguer du code managé](../debugger/debugging-managed-code.md)
- [Types de projet Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
