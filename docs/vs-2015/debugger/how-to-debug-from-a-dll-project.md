---
title: 'Comment : déboguer à partir d’un projet DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839950"
---
# <a name="how-to-debug-from-a-dll-project"></a>Comment : déboguer à partir d'un projet DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour démarrer le débogage d'un projet de DLL, vous devez spécifier l'application appelante dans les propriétés du projet. Les pages de propriétés C++ diffèrent dans la disposition et le contenu par rapport aux pages de propriétés C# et Visual Basic.  
  
 Si une DLL managée est appelée par du code natif et que vous voulez déboguer les deux, vous pouvez le spécifier dans les propriétés du projet. Pour plus d'informations, consultez [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Vous ne pouvez pas spécifier une application appelante externe dans les éditions Express de Visual Studio. Au lieu de cela, vous devez ajouter un projet exécutable à la solution, le définir comme projet de démarrage et appeler les méthodes de votre DLL depuis le projet exécutable.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Pour spécifier l'application appelante dans un projet C++  
  
1. Cliquez avec le bouton droit sur le nœud du projet dans la **Explorateur de solutions** et sélectionnez **Propriétés**. Accédez à l’onglet **Déboguer** .  
  
2. Vérifiez que le champ **Configuration** en haut de la fenêtre est défini sur **Débogage**.  
  
3. Accédez à **Propriétés de configuration/débogage**.  
  
4. Dans la liste **débogueur à lancer** , choisissez débogueur **Windows local** ou **débogueur Windows distant**.  
  
5. Dans la zone commande ou **commande distante** , **Ajoutez le nom** de chemin d’accès complet de l’application.  
  
6. Ajoutez les arguments nécessaires du programme à la zone **Arguments de la commande**.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Pour spécifier l'application appelante dans un projet C# ou Visual basic  
  
1. Cliquez avec le bouton droit sur le nœud du projet dans la **Explorateur de solutions** et sélectionnez **Propriétés**. Accédez à l’onglet **Déboguer** .  
  
     Sélectionnez **Démarrer le programme externe**, puis ajoutez le nom de chemin d’accès complet du programme à exécuter.  
  
     Si vous devez ajouter les arguments de ligne de commande du programme externe, ajoutez-les dans le champ arguments de la **ligne de commande** .  
  
2. Vous pouvez également appeler une application via une URL. (Vous pouvez procéder ainsi si vous déboguez une DLL managée utilisée par une application ASP.NET locale.)  
  
     Sous **action de démarrage**, sélectionnez la case **d’option démarrer le navigateur dans l’URL :** , puis renseignez l’URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Pour démarrer le débogage à partir du projet de DLL  
  
1. Définissez des points d'arrêt selon vos besoins.  
  
2. Démarrez le débogage (appuyez sur F5, cliquez sur la flèche verte ou cliquez sur déboguer **/Démarrer le débogage**).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
