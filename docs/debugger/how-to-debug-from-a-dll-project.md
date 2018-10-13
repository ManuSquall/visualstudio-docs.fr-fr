---
title: 'Comment : déboguer à partir d’un projet de DLL | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2018
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
ms.openlocfilehash: b7b38ac26a07965dc5408c1da1c655a010b6a788
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266186"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Comment : déboguer à partir d’un projet DLL dans Visual Studio

Une façon de déboguer un projet de DLL consiste à spécifier l’application appelante dans les propriétés du projet DLL. Vous pouvez ensuite démarrer le débogage à partir du projet DLL lui-même. Pour cette méthode fonctionne, l’application doit appeler la même DLL dans le même emplacement que celui que vous configurez. Si l’application détecte et charge une version différente de la DLL, cette version ne contient pas vos points d’arrêt. Pour d’autres méthodes de débogage de DLL, consultez [projets DLL de débogage](../debugger/debugging-dll-projects.md).
  
Si votre application managée appelle une DLL native ou votre application native appelle une DLL managée, vous pouvez déboguer la DLL et l’application appelante. Pour plus d’informations, consultez [Comment : déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).   

Les projets DLL natifs et managés ont des paramètres différents pour spécifier les applications appelantes. 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Spécifier une application appelante dans un projet DLL natif  
  
1. Sélectionnez le projet de DLL C++ dans **l’Explorateur de solutions**. Sélectionnez le **propriétés** icône, appuyez sur **Alt**+**entrée**, ou avec le bouton droit et choisissez **propriétés**.
   
1. Dans le  **\<projet > Pages de propriétés** boîte de dialogue zone, assurez-vous que le **Configuration** champ en haut de la fenêtre est défini sur **déboguer**. 
   
1. Sélectionnez **propriétés de Configuration** > **débogage**.  
   
1. Dans le **débogueur à lancer** liste, choisissez **débogueur Windows Local** ou **débogueur Windows distant**.  
   
1. Dans le **commande** ou **commande à distance** zone, ajoutez le chemin d’accès complet et le nom de l’application appelante, comme un *.exe* fichier.
   
   ![Fenêtre de propriétés de débogage](../debugger/media/dbg-debugging-properties-dll.png "fenêtre Propriétés de débogage")  
   
1. Ajoutez les arguments de programme nécessaires à la **Arguments de commande** boîte.  
   
1. Sélectionnez **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Spécifiez une application appelante dans un projet DLL managée  
  
1. Sélectionnez le projet c# ou Visual Basic DLL dans **l’Explorateur de solutions**. Sélectionnez le **propriétés** icône, appuyez sur **Alt**+**entrée**, ou avec le bouton droit et choisissez **propriétés**.
   
1. Assurez-vous que le **Configuration** champ en haut de la fenêtre est défini sur **déboguer**.
   
1. Sous **action de démarrage**:
   
   - Pour des DLL .NET Framework, sélectionnez **démarrer le programme externe**et ajoutez le chemin d’accès complet et le nom de l’application appelante.
     
   - Ou sélectionnez **démarrer le navigateur avec URL** et entrez l’URL d’une application ASP.NET locale. 
   
   - Pour des DLL .NET Core, le **déboguer** page de propriétés est différente. Sélectionnez **exécutable** à partir de la **lancer** liste déroulante, puis ajoutez le chemin d’accès complet et le nom de l’application appelante dans les **exécutable** champ. 
   
1. Ajoutez les arguments de ligne de commande nécessaires dans le **arguments de ligne de commande** ou **arguments Application** champ.
   
   ![Fenêtre Propriétés de débogage c#](../debugger/media/dbg-debugging-properties-dll-csharp.png "fenêtre Propriétés de débogage c#") 
   
1. Utilisez **fichier** > **enregistrer les éléments sélectionnés** ou **Ctrl**+**S** pour enregistrer les modifications.

## <a name="debug-from-the-dll-project"></a>Déboguer à partir du projet DLL  
 
1. Définissez des points d’arrêt dans le projet DLL.

1. Cliquez sur le projet DLL et choisissez **définir comme projet de démarrage**. 

1. Assurez-vous que le **Solutions Configuration** champ est défini sur **déboguer**. Appuyez sur **F5**, cliquez sur le vert **Démarrer** flèche, ou sélectionnez **déboguer** > **démarrer le débogage**.

Si le débogage n’atteint pas vos points d’arrêt, assurez-vous que votre DLL de sortie (par défaut, le  *\<projet > \Debug* dossier) est l’emplacement de l’appel de l’application appelante.
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Paramètres du projet pour les configurations debug c#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)