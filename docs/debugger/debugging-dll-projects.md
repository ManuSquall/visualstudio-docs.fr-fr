---
title: "Débogage de projets DLL | Documents Microsoft"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b43d7c5fb8d66e758a44b86d4918f04599d6147
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Débogage de projets DLL à partir de Visual Studio
Les modèles Visual Studio suivants créent des DLL :  
  
-   (C++, C# et Visual Basic) : bibliothèque de classes   

-   (C++) : projet de DLL de Console Win32
  
     Pour plus d'informations, consultez [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).

-   (C++, C# et Visual Basic) : bibliothèque de contrôles Windows Forms
  
     Débogage d’une bibliothèque de contrôles Windows Forms est semblable au débogage d’un projet de bibliothèque de classes. Dans la plupart des cas, vous appelez le contrôle Windows à partir d'un autre projet. Lorsque vous déboguez le projet appelant, vous pouvez exécuter pas à pas le code de votre contrôle Windows, définir des points d'arrêt et effectuer d'autres opérations de débogage. Pour plus d'informations, consultez [Contrôles Windows Forms](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 Quelle que soit la façon dont vous démarrez le débogage, vérifiez que vous générez d'abord la version Debug de la DLL et que celle-ci se trouve à l'emplacement attendu par l'application. Cette étape semble évidente mais si vous l'omettez, l'application peut rechercher et charger une autre version de la DLL. Le programme continuera alors de s'exécuter, et vous vous demanderez pourquoi votre point d'arrêt n'a pas été atteint. Durant le processus de débogage, vous pouvez vérifier quelles DLL ont été chargées par votre programme en ouvrant la fenêtre **Modules** du débogueur. La fenêtre **Modules** répertorie chaque DLL ou EXE chargé au cours du processus de débogage. Pour plus d'informations, consultez [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
 Pour que le débogueur s'attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 L'application appelante qui appelle votre DLL peut être écrite en code managé ou natif. Si votre DLL managée est appelée par du code natif et que vous souhaitez déboguer les deux types de code, vous devez activer les débogueurs managés et natifs. Vous pouvez sélectionner ceci dans le  **\<projet > Pages de propriétés** boîte de dialogue ou fenêtre. Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante. Pour plus d'informations, consultez [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 Lorsque vous créez un projet d'application console à l'aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [des paramètres de projet pour les Configurations Debug c#](../debugger/project-settings-for-csharp-debug-configurations.md), [paramètres de projet pour une Configuration Debug Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), et [Comment : jeu de Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 Chacun des projets de cette section crée une DLL. Vous ne pouvez pas exécuter une DLL directement, celle-ci doit être appelée par une application, généralement un EXE. Pour plus d'informations, consultez [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects). L'application appelante peut satisfaire un des critères suivants :  
  
-   Une application générée dans un autre projet de la même solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient la bibliothèque de classes.  
  
-   Une application existante déjà déployée sur un ordinateur de test ou de production.  
  
-   Située sur le Web et accessible via une URL.  
  
-   Une application Web qui contient une page Web incorporant la DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
Pour déboguer une DLL, commencez par déboguer l'application appelante, en général il s'agit d'un EXE ou d'une application Web. Pour cela, différentes possibilités s'offrent à vous.  
  
-   Si vous disposez d'un projet pour l'application appelante, vous pouvez ouvrir ce projet et démarrer l'exécution à partir du menu **Debug** . Pour plus d’informations, consultez [mise en route avec le débogueur](../debugger/getting-started-with-the-debugger.md).  
  
-   Si l'application appelante est un programme existant déjà déployé sur un ordinateur de test ou de production et qu'elle est en cours d'exécution, vous pouvez y attacher le débogueur. Utilisez cette méthode si la DLL est un contrôle hébergé par Internet Explorer ou un contrôle sur une page Web. Pour plus d'informations, consultez [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   Vous pouvez la déboguer à partir du projet de DLL. Pour plus d'informations, consultez [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Vous pouvez la déboguer à partir de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [fenêtre exécution](#vxtskdebuggingdllprojectstheimmediatewindow). Dans ce cas, la fenêtre **Exécution** joue le rôle de l'application.  
  
Avant de commencer le débogage de l'application appelante, vous devez généralement définir un point d'arrêt dans la bibliothèque de classes. Pour plus d’informations, consultez [Using Breakpoints](../debugger/using-breakpoints.md). Lorsque le point d'arrêt est atteint, vous pouvez exécuter le code pas à pas, en observant chaque action ligne par ligne, jusqu'à ce que vous ayez isolé le problème. Pour plus d’informations, consultez [parcourir le code dans le débogueur](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> La fenêtre Exécution  
 Vous pouvez évaluer les fonctions ou les méthodes dans la DLL sans application appelante. Effectuez le débogage au moment du design et utilisez la fenêtre **Exécution** . Pour ce type de débogage, suivez la procédure ci-dessous pendant l'ouverture du projet DLL :  
  
1.  Ouvrez la fenêtre **Exécution** du débogueur.  
  
2.  Pour tester une méthode appelée `Test` dans une classe `Class1`, instanciez un objet de type `Class1` en tapant le code C# suivant dans la fenêtre Exécution. Ce code managé fonctionne pour Visual Basic et C++, avec les modifications de syntaxe appropriées :  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     En C#, tous les noms doivent être qualifiés complets. De plus, toutes les méthodes ou variables doivent être dans la portée et le contexte actuels de la session de débogage.  
  
3.  En supposant que `Test` nécessite un paramètre `int` , évaluez `Test` à l'aide de la fenêtre **Exécution** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Le résultat sera imprimé dans la fenêtre **Exécution** .  
  
4.  Vous pouvez continuer à déboguer `Test` en y insérant un point d'arrêt, puis en réévaluant la fonction :  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Une fois le point d'arrêt atteint, vous pourrez exécuter `Test`pas à pas. Lorsque l'exécution aura quitté `Test`, le débogueur repassera en mode Design.

## <a name="vxtskdebuggingdllprojectsexternal"></a>Déboguer une DLL externe à partir d’un projet C++

Si vous déboguez une DLL externe à votre projet, les fonctionnalités de débogage (par exemple, le parcours du code) dépend du [configuration debug de la DLL](#vxtskdebuggingdllprojectsbuildingadebugversion) lorsqu’elle a été créée et si le [le fichier .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) et autres fichiers requis pour la DLL sont disponibles.

Votre projet doit être en mesure de trouver la DLL et le fichier .pdb utilisé pour le débogage. Vous pouvez créer une tâche de génération personnalisée pour copier ces fichiers dans le  **\<dossier du projet > \Debug** dossier de sortie, ou vous pouvez copier les fichiers dans le dossier de sortie manuellement.

Vous pouvez facilement définir les emplacements des fichiers d’en-tête et fichiers de *.lib dans les Pages de propriétés (avec le bouton droit au projet C++ et choisissez **afficher les propriétés**, puis choisissez **toutes les Configurations**) sans avoir à copier les dans votre dossier de sortie :

- Le dossier C/C++ (catégorie Général) - spécifiez le dossier contenant les fichiers d’en-tête dans le **autres répertoires Include** champ.
- Le dossier de l’éditeur de liens (catégorie Général) - spécifiez le dossier contenant le fichier .lib dans le **répertoires de bibliothèques supplémentaires** champ. 
- Le dossier de l’éditeur de liens (catégorie d’entrée) - spécifier le chemin d’accès complet et le nom de fichier pour le fichier .lib dans le **dépendances supplémentaires** champ.

Lors de la configuration est correcte, vous pouvez déboguer en début de l’exécution à partir de la **déboguer** menu.

Pour plus d’informations sur les paramètres de projet, consultez [Pages de propriétés (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projet Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour une Configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)