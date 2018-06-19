---
title: 'Comment : déboguer à partir d’un projet de DLL | Documents Microsoft'
ms.custom: ''
ms.date: 05/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63581cee8816e72492a67a0981a9077b9fec2935
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475809"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Comment : déboguer à partir d’un projet DLL dans Visual Studio
Un pour déboguer un projet DLL consiste à spécifier l’application appelante dans les propriétés de projet du projet DLL et vous pouvez ensuite démarrer le débogage à partir du projet DLL lui-même. Pour cette méthode fonctionne, l’application doit appeler la DLL, et la DLL doit être dans l’emplacement où l’application s’attend à trouver (dans le cas contraire, l’application peut rechercher une autre version de la DLL et qui charge à la place, et il ne sera pas atteint vos points d’arrêt). Pour les autres méthodes de débogage de DLL, consultez [le débogage de projets de DLL](../debugger/debugging-dll-projects.md).
  
Si une DLL managée est appelée par du code natif et que vous voulez déboguer les deux, vous pouvez le spécifier dans les propriétés du projet. Pour plus d'informations, consultez [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).   

Les pages de propriétés C++ diffèrent dans la disposition et le contenu par rapport aux pages de propriétés C# et Visual Basic. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Pour spécifier l'application appelante dans un projet C++  
  
1.  Cliquez sur le nœud du projet dans le **l’Explorateur de solutions** et sélectionnez **propriétés**.  
  
2.  Assurez-vous que le **Configuration** a la valeur de champ en haut de la fenêtre **déboguer**. 

    A **déboguer** configuration est requise pour cette méthode. 
  
3.  Accédez à **propriétés de Configuration > débogage**.  
  
4.  Dans le **débogueur à lancer** , choisissez **débogueur Windows Local** ou **débogueur Windows distant**.  
  
5.  Dans le **commande** ou **commande distante** zone, ajoutez le nom de chemin qualifié complet de l’application appelante (par exemple, un fichier .exe).

    ![Fenêtre Propriétés de débogage](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Ajoutez les arguments de programme nécessaires à la **Arguments de commande** boîte.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Pour spécifier l'application appelante dans un projet C# ou Visual basic  
  
1.  Cliquez sur le nœud du projet dans le **l’Explorateur de solutions** et sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet.

2.  Assurez-vous que le **Configuration** a la valeur de champ en haut de la fenêtre **déboguer**.

3.  (.NET framework) Sélectionnez **démarrer le programme externe**et ajoutez le nom de chemin qualifié complet de l’application appelante.

4.  (.NET core) Sélectionnez **exécutable** à partir de la **lancer** liste, puis ajoutez le nom de chemin qualifié complet de l’application appelante dans les **exécutable** champ. 
  
     Si vous avez besoin d’ajouter des arguments de ligne de commande du programme externe, ajoutez-les dans le **arguments de ligne de commande** (ou **arguments Application**) champ.

    ![Fenêtre Propriétés de débogage](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Si vous le souhaitez, vous pouvez également appeler une application en tant qu’URL. (Vous pouvez procéder ainsi si vous déboguez une DLL managée utilisée par une application ASP.NET locale.)  
  
     Sous **Action de démarrage**, sélectionnez le **démarrer le navigateur avec l’URL :** case d’option et entrez l’URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>Pour démarrer le débogage à partir du projet de DLL  
  
1.  Définir des points d’arrêt dans le projet de DLL. 

2.  Cliquez sur le projet de DLL et choisissez **définir comme projet de démarrage**. 

    (En outre, assurez-vous que le **Solutions Configuration** champ est toujours défini sur **déboguer**.)   
  
3.  Démarrer le débogage (appuyez sur F5, cliquez sur la flèche verte ou **Déboguer > Démarrer le débogage**).

    Vous atteignez les points d’arrêt dans votre DLL. Si vous ne pouvez pas les points d’arrêt, assurez-vous que votre DLL de sortie (par défaut, le **project\Debug** dossier) est dans un emplacement que l’application appelante s’attend à trouver.
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)