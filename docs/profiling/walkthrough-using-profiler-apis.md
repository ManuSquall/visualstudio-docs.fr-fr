---
title: "Proc&#233;dure pas &#224; pas&#160;: utilisation des API du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d'analyse des performances, procédures pas à pas"
  - "outils de profilage, procédures pas à pas"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Proc&#233;dure pas &#224; pas&#160;: utilisation des API du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La procédure pas à pas utilise une application C\# pour illustrer l'utilisation des API des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vous utiliserez les API du profileur pour limiter la quantité de données collectées pendant le profilage par instrumentation.  
  
 Les étapes dans cette procédure pas à pas s'appliquent généralement à une application C\/C\+\+.  Vous devrez configurer votre environnement de génération en fonction de chaque langage.  
  
 En général, il est recommandé de commencer par analyser la performance de l'application à l'aide de l'exemple de profilage.  Si celui\-ci ne fournit pas les informations qui définissent un goulot d'étranglement, le profilage par instrumentation peut fournir un niveau supérieur de détail.  Le profilage par instrumentation est très utile pour enquêter sur l'interaction de thread.  
  
 Toutefois, un niveau supérieur de détail entraîne un plus grand nombre de données rassemblées.  Vous constaterez sans doute que le profilage par instrumentation crée de grands fichiers de données.  L'instrumentation est également plus susceptible d'avoir un impact sur la performance de l'application.  Pour plus d'informations, consultez [Fonctionnement des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md) et [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md).  
  
 Le profileur Visual Studio vous permet de limiter la collecte de données.  Cette procédure pas à pas illustre la façon de limiter la collecte de données en utilisant les API du profileur.  Le profileur Visual Studio fournit une API pour contrôler la collecte de données depuis une application.  
  
 Pour le code natif, les API du profileur Visual Studio se trouvent dans VSPerf.dll.  Le fichier d'en\-tête, VSPerf.h, et la bibliothèque d'importation, VSPerf.lib, se trouvent dans le répertoire Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
 Pour un code managé, les API du profileur se trouvent dans Microsoft.VisualStudio.Profiler.dll.  Cette DLL se trouve dans le répertoire Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Profiler>.  
  
## Composants requis  
 Cette procédure pas à pas présuppose que votre choix d'environnement de développement est configuré pour prendre en charge le débogage et l'échantillonnage.  Les rubriques suivantes fournissent une vue d'ensemble de ces conditions préalables :  
  
 [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)  
  
 [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Par défaut, lors de son lancement, le profileur collecte des données au niveau global.  Le code suivant désactive le profilage global au début du programme.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Vous pouvez désactiver la collecte de données à la ligne de commande sans utiliser un appel d'API.  Les étapes suivantes supposent que votre environnement de génération de la ligne de commande est configuré pour exécuter les outils de profilage et vos outils de développement.  Cela inclut les paramètres nécessaires pour VSInstr et VSPerfCmd.  Consultez Outils de profilage de ligne de commande.  
  
## Limiter la collecte de données à l'aide des API du profileur  
  
#### Pour créer le code à profiler  
  
1.  Créez un nouveau projet C\# dans Visual Studio ou utilisez une génération de ligne de commande, selon votre préférence.  
  
    > [!NOTE]
    >  La build doit faire référence à la bibliothèque Microsoft.VisualStudio.Profiler.dll, située dans le répertoire Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
2.  Copiez et collez le code suivant dans votre projet :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### Pour collecter et consulter des données dans l'IDE de Visual Studio  
  
1.  Ouvrez l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dans le menu **Analyser**, pointez sur **Profileur**, puis cliquez sur **Nouvelle session de performance**.  
  
2.  Ajoutez votre fichier compilé à la liste **Cibles** dans la fenêtre **Explorateur de performances**.  Cliquez avec le bouton droit sur **Cibles**, puis cliquez sur **Ajouter un fichier binaire cible**.  Localisez le fichier binaire dans la boîte de dialogue **Ajouter un fichier binaire cible**, puis cliquez sur **Ouvrir**.  
  
3.  Sélectionnez **Instrumentation** dans la liste **Méthode** de la barre d'outils de l'**Explorateur de performances**.  
  
4.  Cliquez sur **Démarrer avec le profilage**.  
  
     Le profileur instrumente et exécute le fichier binaire et crée un fichier de rapport de performances,  qui apparaît dans le nœud **Rapports** de l'**Explorateur de performances**.  
  
5.  Ouvrez le fichier de rapport de performances résultant.  
  
 Par défaut, lors de son lancement, le profileur collecte des données au niveau global.  Le code suivant désactive le profilage global au début du programme.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### Pour rassembler et consulter des données à la ligne de commande  
  
1.  Compilez une version Debug de l'exemple de code que vous avez créée au cours de la procédure "Pour créer un code à profiler", plus haut.  
  
2.  Pour profiler une application managée, tapez la commande suivante pour définir les variables d'environnement appropriées :  
  
     VsPefCLREnv \/traceon  
  
3.  Tapez la commande suivante :VSInstr \<NomFichier\>.exe  
  
4.  Tapez la commande suivante : VSPerfCmd \/start:trace \/output:\<NomFichier\>.vsp  
  
5.  Tapez la commande suivante :VSPerfCmd \/globaloff  
  
6.  Exécutez votre programme.  
  
7.  Tapez la commande suivante :VSPerfCmd \/shutdown  
  
8.  Tapez la commande suivante :VSPerfReport \/calltrace:\<NomFichier\>.vsp  
  
     Un fichier .csv est créé dans le répertoire actif avec les données de performances résultantes.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Prise en main](../profiling/getting-started-with-performance-tools.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)