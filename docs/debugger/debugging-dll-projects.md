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
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450411"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Déboguer des dll dansC#Visual C++Studio (, F#, Visual Basic,)

Une DLL (bibliothèque de liens dynamiques) est une bibliothèque qui contient le code et les données qui peuvent être utilisés par plusieurs applications. Vous pouvez utiliser Visual Studio pour créer, générer, configurer et déboguer des dll.

## <a name="create-a-dll"></a>Créer une DLL

Les modèles de projet Visual Studio suivants peuvent créer des dll :

- C#Bibliothèque de classes, F# Visual Basic ou
- C#ou Visual Basic bibliothèque de contrôle de Windows Forms (WCF)
- C++Bibliothèque de liens dynamiques (DLL)

Pour plus d’informations, consultez [Techniques de débogage de MFC](../debugger/mfc-debugging-techniques.md).

Le débogage d’une bibliothèque WCF est semblable au débogage d’une bibliothèque de classes. Pour plus d’informations, consultez [Windows Forms des contrôles](/dotnet/framework/winforms/controls/index).

En général, vous appelez une DLL à partir d’un autre projet. Lorsque vous déboguez le projet appelant, en fonction de la configuration de la DLL, vous pouvez effectuer un pas à pas détaillé et déboguer le code de la DLL.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuration de débogage de DLL

Quand vous utilisez un modèle de projet Visual Studio pour créer une application, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations de build Debug et Release. Vous pouvez modifier ces paramètres si nécessaire. Pour plus d’informations, consultez les articles suivants :

- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Set C++ DebuggableAttribute

Pour que le débogueur s’attache à C++ une dll, C++ le code doit émettre `DebuggableAttribute`.

**Pour définir `DebuggableAttribute`:**

1. Sélectionnez le C++ projet DLL dans **Explorateur de solutions** et sélectionnez l’icône **Propriétés** , ou cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.

1. Dans le volet **Propriétés** , sous **éditeur de liens** > **débogage**, sélectionnez **Oui (/ASSEMBLYDEBUG)** pour l' **assembly pouvant être débogué**.

Pour plus d’informations, consultez [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a>Définir les emplacementsC++ des fichiers C/dll

Pour déboguer une DLL externe, un projet appelant doit être en mesure de trouver la DLL, son [fichier. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)et tout autre fichier requis par la dll. Vous pouvez créer une tâche de génération personnalisée pour copier ces fichiers dans votre *dossier de projet\<>* dossier de sortie \Debug., ou vous pouvez copier les fichiers manuellement.

Pour C/C++ Projects, vous pouvez définir les emplacements des fichiers d’en-tête et lib dans les pages de propriétés du projet, au lieu de les copier dans le dossier de sortie.

**Pour définir les emplacementsC++ de fichier C/Header et lib :**

1. Sélectionnez le projet CC++ /DLL dans **Explorateur de solutions** et sélectionnez l’icône **Propriétés** , ou cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.

1. En haut du volet **Propriétés** , sous **configuration**, sélectionnez **toutes les configurations**.

1. Sous **C/C++**  > **général** > **autres répertoires Include**, spécifiez le dossier qui contient des fichiers d’en-tête.

1. Sous **éditeur de liens** > **général** > **répertoires de bibliothèques supplémentaires**, spécifiez le dossier qui contient des fichiers lib.

1. Sous l' **éditeur de liens** > **d’entrée** > **des dépendances supplémentaires**, spécifiez le chemin d’accès complet et le nom de fichier pour les fichiers lib.

1. Sélectionnez **OK**.

Pour plus d’informations C++ sur les paramètres du projet, consultez Référence de la [page de propriétés Windows C++ ](/cpp/build/reference/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Générer une version de débogage

Veillez à créer une version de débogage de la DLL avant de commencer le débogage. Pour déboguer une DLL, une application appelante doit être en mesure de trouver son [fichier. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et tous les autres fichiers requis par la dll.

Vous pouvez créer une tâche de génération personnalisée pour copier les fichiers DLL dans votre *\<appelant le dossier du projet >* dossier de sortie \Debug., ou vous pouvez copier les fichiers manuellement.

Veillez à appeler la DLL à l’emplacement approprié. Cela peut paraître évident, mais si une application appelante trouve et charge une copie différente de la DLL, le débogueur n’atteint jamais les points d’arrêt que vous définissez.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Déboguer une DLL

Vous ne pouvez pas exécuter une DLL directement. Elle doit être appelée par une application, généralement un fichier *. exe* . Pour plus d’informations, consultez [projets Visual Studio C++- ](/cpp/ide/creating-and-managing-visual-cpp-projects).

Pour déboguer une DLL, vous pouvez [Démarrer le débogage à partir de l’application appelante](#vxtskdebuggingdllprojectsthecallingapplication), ou [Déboguer à partir du projet dll](how-to-debug-from-a-dll-project.md) en spécifiant son application appelante. Vous pouvez également utiliser la [fenêtre exécution](#vxtskdebuggingdllprojectstheimmediatewindow) du débogueur pour évaluer les fonctions ou les méthodes de la dll au moment du design, sans utiliser une application appelante.

Pour plus d’informations, consultez [premier aperçu du débogueur](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Démarrer le débogage à partir de l’application appelante

L’application qui appelle une DLL peut être :

- Application d’un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la même solution ou dans une autre solution de la DLL.
- Une application existante déjà déployée et en cours d’exécution sur un ordinateur de test ou de production.
- Située sur le web et accessible via une URL.
- Une application Web avec une page Web qui incorpore la DLL.

Pour déboguer une DLL à partir d’une application appelante, vous pouvez :

- Ouvrez le projet pour l’application appelante et démarrez le débogage en sélectionnant **Déboguer** > **Démarrer le débogage** ou en appuyant sur **F5**.

  or

- Attachement à une application déjà déployée et en cours d’exécution sur un ordinateur de test ou de production. Utilisez cette méthode pour les dll sur des sites Web ou dans des applications Web. Pour plus d’informations, consultez [Guide pratique pour attacher à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Avant de commencer le débogage de l’application appelante, définissez un point d’arrêt dans la DLL. Consultez [utilisation de points d’arrêt](../debugger/using-breakpoints.md). Lorsque le point d’arrêt de la DLL est atteint, vous pouvez exécuter le code pas à pas, en observant l’action sur chaque ligne. Pour plus d’informations, consultez [Parcourir le code dans le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

Pendant le débogage, vous pouvez utiliser la fenêtre **modules** pour vérifier les dll et les fichiers *. exe* chargés par l’application. Pour ouvrir la fenêtre **modules** , pendant le débogage, sélectionnez **déboguer** > **modules** **Windows** > . Pour plus d’informations, consultez [Guide pratique pour utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Utiliser la fenêtre exécution

Vous pouvez utiliser la fenêtre **exécution** pour évaluer les fonctions ou les méthodes de la dll au moment de la conception. La fenêtre **exécution** joue le rôle d’une application appelante.

>[!NOTE]
>Vous pouvez utiliser la fenêtre **exécution** au moment du design avec la plupart des types de projet. Elle n’est pas prise en charge pour SQL, les projets Web ou les scripts.

Par exemple, pour tester une méthode nommée `Test` dans la classe `Class1`:

1. Une fois le projet DLL ouvert, ouvrez la fenêtre **exécution** en sélectionnant **déboguer** > **Windows** > **immédiat** ou en appuyant sur **CTRL**+**ALT**+**I**.

1. Instanciez un objet de type `Class1` en tapant le C# code suivant dans la fenêtre **exécution** et en appuyant sur **entrée**. Ce code managé fonctionne pour C# et Visual Basic, avec les modifications de syntaxe appropriées :

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, tous les noms doivent être qualifiés complets. Toutes les méthodes ou variables doivent être dans la portée et le contexte actuels lorsque le service de langage tente d’évaluer l’expression.

1. En supposant que `Test` nécessite un paramètre `int` , évaluez `Test` à l'aide de la fenêtre **Exécution** :

   ```csharp
   ?obj.Test(10);
   ```

   Le résultat s’imprime dans la fenêtre **exécution** .

1. Vous pouvez continuer à déboguer `Test` en y insérant un point d’arrêt, puis en réévaluant la fonction.

   Le point d’arrêt est atteint et vous pouvez effectuer un pas à pas détaillé `Test`. Une fois que l’exécution a quitté `Test`, le débogueur repasse en mode Création.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Débogage en mode mixte

Vous pouvez écrire une application appelante pour une DLL en code managé ou natif. Si votre application native appelle une DLL managée et que vous souhaitez déboguer les deux, vous pouvez activer les débogueurs managés et natifs dans les propriétés du projet. Le processus exact varie selon que vous souhaitez démarrer le débogage à partir du projet DLL ou du projet de l’application appelante. Pour plus d’informations, consultez [Guide pratique pour déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).

Vous pouvez également déboguer une DLL native à partir d’un projet appelant managé. Pour plus d’informations, consultez [Comment déboguer du code managé et natif](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Voir aussi
- [Déboguer du code managé](../debugger/debugging-managed-code.md)
- [Préparer le débogage C++ de projets](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
