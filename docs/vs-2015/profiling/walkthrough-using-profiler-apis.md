---
title: 'Procédure pas à pas : utilisation des API du profileur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5fc0f5a11d29fdb1ee570dc32066fdd492ed8db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871536"
---
# <a name="walkthrough-using-profiler-apis"></a>Procédure pas à pas : utilisation des API du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La procédure pas à pas utilise une application C# pour montrer comment utiliser les API des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous utilisez les API du profileur pour limiter la quantité de données collectées pendant le profilage par instrumentation.

 Les étapes décrites dans cette procédure pas à pas s’appliquent généralement à une application C/C++. Vous devez configurer votre environnement de génération de façon appropriée pour chaque langage.

 En règle générale, vous commencez par analyser les performances d’une application avec un profilage par échantillonnage. Si le profilage par échantillonnage ne fournit pas d’informations permettant de localiser un goulot d’étranglement, le profilage par instrumentation peut fournir un niveau de détail plus élevé. Le profilage par instrumentation est très pratique pour examiner l’interaction des threads.

 Cependant, un niveau de détail plus élevé signifie que plus de données sont collectées. Vous constaterez peut-être que le profilage par instrumentation crée des fichiers de données volumineux. En outre, l’instrumentation est plus susceptible d’avoir un impact sur les performances de l’application. Pour plus d’informations, consultez [Présentation des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md) et [Présentation des valeurs des données d’échantillonnage](../profiling/understanding-sampling-data-values.md)

 Le profileur Visual Studio vous permet de limiter la collecte des données. Cette procédure pas à pas illustre la façon de limiter la collecte de données en utilisant les API du profileur. Le profileur Visual Studio fournit une API pour contrôler la collecte de données depuis une application.

 Pour le code natif, les API du profileur Visual Studio se trouvent dans VSPerf.dll. Le fichier d’en-tête, VSPerf.h, et la bibliothèque d’importation, VSPerf.lib, se trouvent dans le répertoire Microsoft Visual Studio 9\Team Tools\Performance Tools.

 Pour le code managé, les API du profileur se trouvent dans Microsoft.VisualStudio.Profiler.dll. Cette DLL se trouve dans le répertoire Microsoft Visual Studio 9\Team Tools\Performance Tools. Pour plus d'informations, consultez [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Prérequis
 Cette procédure pas à pas suppose que votre environnement de développement est configuré pour prendre en charge le débogage et l’échantillonnage. Les rubriques suivantes fournissent une vue d’ensemble de ces prérequis :

 [Guide pratique pour choisir une méthode de collecte](../profiling/how-to-choose-collection-methods.md)

 [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)

 Par défaut, quand le profileur est démarré, il collecte des données au niveau global. Le code suivant au début du programme désactive le profilage global.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Vous pouvez désactiver la collecte de données sur la ligne de commande sans utiliser un appel d’API. Les étapes suivantes supposent que votre environnement de génération de ligne de commande est configuré pour exécuter les outils de profilage et vos outils de développement. Ceci inclut les paramètres nécessaires pour VSInstr et VSPerfCmd. Consultez Outils de profilage en ligne de commande.

## <a name="limiting-data-collection-using-profiler-apis"></a>Limitation de la collecte de données avec les API du profileur

#### <a name="to-create-the-code-to-profile"></a>Pour créer le code à profiler

1. Créez un projet C# dans Visual Studio ou utilisez une génération en ligne de commande, selon ce que vous préférez.

    > [!NOTE]
    > Votre build doit référencer la bibliothèque Microsoft.VisualStudio.Profiler.dll, qui se trouve dans le répertoire Microsoft Visual Studio 9\Team Tools\Performance Tools.

2. Copiez et collez le code suivant dans votre projet :

    ```csharp
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

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Pour collecter et afficher des données dans l’IDE Visual Studio

1. Ouvrez l’IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dans le menu **Analyser**, pointez sur **Profileur**, puis cliquez sur **Nouvelle session de performance**.

2. Ajoutez votre fichier binaire compilé à la liste **Cibles** dans la fenêtre **Explorateur de performances**. Cliquez avec le bouton droit sur **Cibles**, puis sélectionnez **Ajouter un fichier binaire cible**. Recherchez le fichier binaire dans la boîte de dialogue **Ajouter un fichier binaire cible**, puis cliquez sur **Ouvrir**.

3. Sélectionnez **Instrumentation** dans la liste **Méthode** sur la barre d’outils de **l’Explorateur de performances**.

4. Cliquez sur **Démarrer avec le profilage**.

    Le profileur instrumente et exécute le fichier binaire, et crée un fichier de rapport des performances. Le fichier du rapport de performances apparaît dans le nœud **Rapports** de **l’Explorateur de performances**.

5. Ouvrez le fichier de rapport de performances résultant.

   Par défaut, quand le profileur est démarré, il collecte des données au niveau global. Le code suivant au début du programme désactive le profilage global.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Pour collecter et visualiser des données sur la ligne de commande

1. Compilez une version debug de l’exemple de code que vous avez créé dans la procédure « Création de code à profiler », plus haut dans cette procédure pas à pas.

2. Pour profiler une application managée, tapez la commande suivante pour définir les variables d’environnement appropriées :

     **VsPefCLREnv /traceon**

3. Tapez la commande suivante :**VSInstr \<filename> . exe**

4. Tapez la commande suivante :**VSPerfCmd/start : trace/output : \<filename> . vsp**

5. Tapez la commande suivante : **VSPerfCmd /globaloff**

6. Exécutez votre programme.

7. Tapez la commande suivante : **VSPerfCmd /shutdown**

8. Tapez la commande suivante :**VSPerfReport/calltrace : \<filename> . vsp**

     Un fichier .csv est créé dans le répertoire actif avec les données de performances résultantes.

## <a name="see-also"></a>Voir aussi

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Informations de référence sur l’API du profileur Visual Studio (natif)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Prise en main](../profiling/getting-started-with-performance-tools.md)
- [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)