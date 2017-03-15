---
title: "D&#233;bogage de projets DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer des DLL"
  - "modèles, déboguer des DLL"
  - "DLL, débogage"
  - "débogage [Visual Studio], DLL"
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage de projets DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les modèles suivants créent des DLL :  
  
-   \(C\+\+, C\# et Visual Basic\) : bibliothèque de classes  
  
-   \(C\+\+, C\# et Visual Basic\) : bibliothèque de contrôles Windows Forms  
  
     Le débogage d'une bibliothèque de contrôles Windows est semblable à celui d'un projet Bibliothèque de classes. Dans la plupart des cas, vous appelez le contrôle Windows à partir d'un autre projet. Lorsque vous déboguez le projet appelant, vous pouvez exécuter pas à pas le code de votre contrôle Windows, définir des points d'arrêt et effectuer d'autres opérations de débogage. Pour plus d'informations, consultez [Contrôles Windows Forms](../Topic/Windows%20Forms%20Controls.md).  
  
-   \(C\# et Visual Basic\) : bibliothèque de contrôles Web  
  
     Pour plus d'informations, consultez [Bibliothèque de contrôles Web \(code managé\)](../debugger/web-control-library-managed-code.md).  
  
-   \(C\+\+\) : contrôle Active X MFC et contrôle ActiveX Smart Device MFC  
  
     Les contrôles ActiveX sont des contrôles téléchargeables depuis Internet sur un ordinateur client et qui peuvent être affichés et activés sur des pages Web.  
  
     Leur débogage est semblable à celui d'autres types de contrôles dans la mesure où ils ne peuvent pas être exécutés comme des applications autonomes, mais qu'ils doivent être incorporés dans une page Web HTML. Pour plus d'informations, consultez [Comment : déboguer un contrôle ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
-   \(C\+\+\) : DLL Smart Device MFC  
  
     Pour plus d'informations, consultez [Techniques de débogage MFC](../debugger/mfc-debugging-techniques.md).  
  
 Cette section contient également des informations sur les rubriques suivantes :  
  
-   [Comment : déboguer à partir d'un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
-   [Comment : déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md)  
  
 Cette rubrique contient les sections suivantes qui réunissent des informations relatives à la préparation du débogage des bibliothèques de classes :  
  
-   [Génération d'une version Debug](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
-   [Débogage en mode mixte](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
-   [Modification des configurations par défaut](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
-   [Procédures pour déboguer la DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
-   [Application appelante](#vxtskdebuggingdllprojectsthecallingapplication)  
  
-   [Contrôles sur une page Web](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
-   [La fenêtre Exécution](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Génération d'une version Debug  
 Quelle que soit la façon dont vous démarrez le débogage, vérifiez que vous générez d'abord la version Debug de la DLL et que celle\-ci se trouve à l'emplacement attendu par l'application. Cette étape semble évidente mais si vous l'omettez, l'application peut rechercher et charger une autre version de la DLL. Le programme continuera alors de s'exécuter, et vous vous demanderez pourquoi votre point d'arrêt n'a pas été atteint. Durant le processus de débogage, vous pouvez vérifier quelles DLL ont été chargées par votre programme en ouvrant la fenêtre **Modules** du débogueur. La fenêtre **Modules** répertorie chaque DLL ou EXE chargé au cours du processus de débogage. Pour plus d'informations, consultez [Comment : utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md).  
  
 Pour que le débogueur s'attache au code écrit en C\+\+, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Débogage en mode mixte  
 L'application appelante qui appelle votre DLL peut être écrite en code managé ou natif. Si votre DLL managée est appelée par du code natif et que vous souhaitez déboguer les deux types de code, vous devez activer les débogueurs managés et natifs. Vous pouvez sélectionner ceci dans la boîte de dialogue ou la fenêtre **Pages de propriétés** de **\<Projet\>**. Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante. Pour plus d'informations, consultez [Comment : déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Modification des configurations par défaut  
 Lorsque vous créez un projet d'application console à l'aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Pour plus d'informations, voir [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md), [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) et [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Procédures pour déboguer la DLL  
 Chacun des projets de cette section crée une DLL. Vous ne pouvez pas exécuter une DLL directement, celle\-ci doit être appelée par une application, généralement un EXE. Pour plus d'informations, consultez [Création et gestion de projets Visual C\+\+](/visual-cpp/ide/creating-and-managing-visual-cpp-projects). L'application appelante peut satisfaire un des critères suivants :  
  
-   Une application générée dans un autre projet de la même solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient la bibliothèque de classes.  
  
-   Une application existante déjà déployée sur un ordinateur de test ou de production.  
  
-   Située sur le Web et accessible via une URL.  
  
-   Une application Web qui contient une page Web incorporant la DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Débogage de l'application appelante  
 Pour déboguer une DLL, commencez par déboguer l'application appelante, en général il s'agit d'un EXE ou d'une application Web. Pour cela, différentes possibilités s'offrent à vous.  
  
-   Si vous disposez d'un projet pour l'application appelante, vous pouvez ouvrir ce projet et démarrer l'exécution à partir du menu **Debug**. Pour plus d'informations, consultez [How to: Start Execution](http://msdn.microsoft.com/fr-fr/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
-   Si l'application appelante est un programme existant déjà déployé sur un ordinateur de test ou de production et qu'elle est en cours d'exécution, vous pouvez y attacher le débogueur. Utilisez cette méthode si la DLL est un contrôle hébergé par Internet Explorer ou un contrôle sur une page Web. Pour plus d'informations, consultez [How to: Attach to a Running Process](http://msdn.microsoft.com/fr-fr/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
-   Vous pouvez la déboguer à partir du projet de DLL. Pour plus d'informations, consultez [Comment : déboguer à partir d'un projet DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Vous pouvez la déboguer à partir de la fenêtre **Exécution** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans ce cas, la fenêtre **Exécution** joue le rôle de l'application.  
  
 Avant de commencer le débogage de l'application appelante, vous devez généralement définir un point d'arrêt dans la bibliothèque de classes. Pour plus d'informations, consultez [Breakpoints and Tracepoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583). Lorsque le point d'arrêt est atteint, vous pouvez exécuter le code pas à pas, en observant chaque action ligne par ligne, jusqu'à ce que vous ayez isolé le problème. Pour plus d'informations, consultez [Code Stepping Overview](http://msdn.microsoft.com/fr-fr/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Contrôles sur une page Web  
 Pour déboguer un contrôle de page Web, créez une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui l'incorpore si elle n'existe pas déjà. Puis, placez des points d'arrêt dans le code de la page Web ainsi que dans le code du contrôle. Vous appelez alors la page Web à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Avant de commencer le débogage de l'application appelante, vous devez généralement définir un point d'arrêt dans la DLL. Lorsque le point d'arrêt est atteint, vous pouvez exécuter le code pas à pas, en observant chaque action ligne par ligne, jusqu'à ce que vous ayez isolé le problème. Pour plus d'informations, consultez [Breakpoints and Tracepoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> La fenêtre Exécution  
 Vous pouvez évaluer les fonctions ou les méthodes dans la DLL sans application appelante. Effectuez le débogage au moment du design et utilisez la fenêtre **Exécution**. Pour ce type de débogage, suivez la procédure ci\-dessous pendant l'ouverture du projet DLL :  
  
1.  Ouvrez la fenêtre **Exécution** du débogueur.  
  
2.  Pour tester une méthode appelée `Test` dans une classe `Class1`, instanciez un objet de type `Class1` en tapant le code C\# suivant dans la fenêtre Exécution. Ce code managé fonctionne pour Visual Basic et C\+\+, avec les modifications de syntaxe appropriées :  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     En C\#, tous les noms doivent être qualifiés complets. De plus, toutes les méthodes ou variables doivent être dans la portée et le contexte actuels de la session de débogage.  
  
3.  En supposant que `Test` nécessite un paramètre `int`, évaluez `Test` à l'aide de la fenêtre **Exécution** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Le résultat sera imprimé dans la fenêtre **Exécution**.  
  
4.  Vous pouvez continuer à déboguer `Test` en y insérant un point d'arrêt, puis en réévaluant la fonction :  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Une fois le point d'arrêt atteint, vous pourrez exécuter `Test` pas à pas. Lorsque l'exécution aura quitté `Test`, le débogueur repassera en mode Design.  
  
## Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets Visual C\+\+](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Types de projets C\#, F\# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)