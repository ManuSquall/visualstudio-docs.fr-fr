---
title: 'Procédure pas à pas : utilisation d’IntelliTrace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839606"
---
# <a name="walkthrough-using-intellitrace"></a>Procédure pas à pas : utilisation d'IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser IntelliTrace pour collecter des informations sur des événements spécifiques ou des catégories d'événements, ou sur des appels de fonction individuels en plus d'événements. Les procédures suivantes montrent comment procéder.  
  
 Vous pouvez utiliser IntelliTrace dans Visual Studio Enterprise Edition (mais pas dans les éditions Professional ou Community).  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> Utilisation d'IntelliTrace avec seulement des événements  
 Vous pouvez essayer de déboguer avec seulement les événements IntelliTrace. Les événements IntelliTrace sont des événements de débogueur, des exceptions, des événements .NET Framework et d'autres événements système. Avant de commencer le débogage, vous devez activer ou désactiver des événements spécifiques pour contrôler les événements qu'IntelliTrace enregistre. Pour plus d’informations, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  
  
 Les étapes suivantes montrent comment déboguer avec seulement les événements IntelliTrace :  
  
1. Activez l'événement IntelliTrace pour l'accès aux fichiers. Accédez à la page **Outils / Options / IntelliTrace / Événements IntelliTrace** , puis développez la catégorie **Fichier** . Cochez la catégorie d'événements **Fichier** . Ainsi, tous les événements concernant les fichiers (accès, fermeture, suppression) sont cochés.  
  
2. Créez une application console C#. Ouvrez le fichier Program.cs et ajoutez l'instruction `using` suivante :  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Créez un <xref:System.IO.FileStream> dans la méthode Main, lisez dans ce flux, fermez-le et supprimez le fichier. Ajoutez une autre ligne juste pour avoir un emplacement où définir un point d'arrêt :  
  
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
  
4. Définissez un point d'arrêt sur `Console.WriteLine("done");`  
  
5. Démarrez le débogage selon la procédure habituelle. (Appuyez sur **F5** ou cliquez sur **Déboguer / Démarrer le débogage**.  
  
    > [!TIP]
    > Gardez les fenêtres **Variables locales** et **Automatique** ouvertes pendant que vous déboguez pour voir et enregistrer les valeurs qui s'y affichent.  
  
6. L’exécution s’interrompt au point d’arrêt. Si vous ne voyez pas la fenêtre **Outils de diagnostic** , cliquez sur **Déboguer / Fenêtres / Événements IntelliTrace**.  
  
     Dans la fenêtre **Outils de diagnostic** , recherchez l'onglet **Événements** (vous voyez normalement trois onglets, **Événements**, **Utilisation de la mémoire**et **Utilisation de l'UC**). L'onglet **Événements** affiche une liste chronologique des événements, qui se termine par le dernier événement avant que le débogueur ait interrompu l'exécution. Vous devez voir un événement nommé **Accès à WordSearchInputs.txt**.  
  
     La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.  
  
     ![Update 1 IntelliTrace&#45;](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
7. Sélectionnez l'événement pour développer ses détails.  
  
     La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Vous pouvez choisir le lien de chemin d'accès pour ouvrir le fichier. Si le chemin d'accès complet n'est pas disponible, la boîte de dialogue **Ouvrir un fichier** s'affiche.  
  
     Cliquez sur **Activer le débogage d'historique**, qui définit le contexte du débogueur au moment où l'événement sélectionné a été collecté, en affichant les données de l'historique dans les fenêtres **Pile des appels**et **Variables locales** , ainsi que dans les autres fenêtres concernées du débogueur. Si le code source est disponible, Visual Studio déplace le pointeur jusqu'au code correspondant dans la fenêtre source afin de vous permettre de l'examiner.  
  
     La capture d’écran suivante a été faite à partir de Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
8. Si vous ne trouvez pas le bogue, essayez de tester d'autres événements aboutissant au bogue. IntelliTrace peut également enregistrer des informations sur les appels pour vous permettre de parcourir pas à pas les appels de fonction.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Utilisation d'IntelliTrace avec des événements et des appels de fonctions  
 IntelliTrace peut enregistrer les appels de fonction ainsi que les événements. Cette opération vous permet de consulter l'historique de la pile des appels et de vous déplacer vers l'arrière ou vers l'avant dans les appels de votre code. IntelliTrace enregistre des données comme les noms des fonctions, les points d'entrée et de sortie des fonctions, ainsi que certaines valeurs de paramètres et de retour. Consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  
  
1. Activez la collecte d'appels. (Dans **Outils / Options / IntelliTrace / Général**, sélectionnez **Informations sur les événements et les appels d'IntelliTrace**. IntelliTrace va commencer à collecter ces informations au démarrage de la session de débogage suivante.  
  
    > [!TIP]
    > Cette opération peut ralentir votre application et augmenter la taille de tous les fichiers journaux IntelliTrace (fichiers .iTrace) que vous enregistrez sur le disque. Pour obtenir le maximum de données d'appel tout en réduisant les effets indésirables, enregistrez uniquement les données des modules qui vous intéressent. Pour modifier la taille maximale de vos fichiers .iTrace, accédez à **Outils / Options / IntelliTrace / Avancé**et spécifiez la quantité maximale d'espace disque. La valeur par défaut est 250 Mo.  
  
2. Démarrez le débogage de l'application de console C# créée dans la section précédente. L’exécution s’interrompt au point d’arrêt. Si vous ne voyez pas la fenêtre **Outils de diagnostic** , cliquez sur **Déboguer / Fenêtres / Événements IntelliTrace**.  
  
3. Basculez vers l’onglet **Appels** .  
  
     Vous voyez maintenant les appels de fonction de votre application, qui commencent par l'appel racine (dans la solution actuelle, le point d'entrée de Main) et se terminent par l'emplacement où l'exécution s'est arrêtée.  
  
     Sélectionnez l'un des appels de fonction et double-cliquez dessus. Vous devez voir les points d'entrée et de sortie de la fonction, ainsi que les appels que l'appel actuel a fait à d'autres fonctions et les événements IntelliTrace déclenchés par l'appel. Si vous n'avez pas activé le débogage d'historique, cette action l'active. Pour plus d’informations sur le débogage d’historique, consultez [Historical Debugging](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > Vous pouvez voir que certains appels apparaissent grisés. La raison en est qu'IntelliTrace n'a pas enregistré les données des modules correspondants. Pour consulter ces données, configurez IntelliTrace de manière à collecter les données de ces modules. Pour plus d’informations sur la spécification des modules, consultez [fonctionnalités IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Étapes suivantes
